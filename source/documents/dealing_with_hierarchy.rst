Dealing with hierarchy
======================

How to handle internal pointers to native instances and multiple inheritance ?
------------------------------------------------------------------------------

What is that all about ?
^^^^^^^^^^^^^^^^^^^^^^^^

When multiple extension classes inherit to each other, the inherited classes end up with a growing number of internal pointer. Let's explain with a concrete example: sf.Window and sf.RenderWindow.

sf.Window wraps the native sf::Window type and therefore has an internal pointer to sf::Window.
sf::RenderWindow wraps the native sf::RenderWindow and inherits from sf.Window, therefore it has two internal pointers, one to sf::Window and the second to sf::RenderWindow.

Cython offers two constructors and one destructor: ```__init__```, ```__cinit__```, ```__dealloc__```. Their behaviors is well defined but rigid. We can't prevent ```__cinit__``` or ```__dealloc__``` from being called or we can't recall them.

As we can't mess up the internal pointer of a parent class and as we're quite stuck in this strict behavior, we'll need to carefully respect some rules, which are, by the way, only related to this bindings and these are part of its convention.

_**Note:** There's a document on the Cython wiki (http://wiki.cython.org/WrappingSetOfCppClasses) but I wasn't satisfied. He ends up with multiple useless allocation/deallocation to solve common issues..._

Introduction
^^^^^^^^^^^^
Let's see a snippet summarizing what we've said so far::

    class Window:
        cdef sf.Window *p_window

        def __cinit__(self): pass
        def __init__(self): pass
        def __dealloc__(self): pass

    class RenderWindow(Window):
        cdef sf.RenderWindow *p_renderwindow
        # we have here acess to p_window, of course.

        def __cinit__(self): pass
        def __init__(self): pass
        def __dealloc__(self): pass

When I create/destroy a sf.RenderWindow, here are the initialization/termination order::

    Window::__cinit__()
    RenderWindow::__cinit__()
    RenderWindow::__init__()
    …
    RenderWindow::__dealloc__()
    Window::__dealloc__()

_**Note:** we could call Window::__init__() from RenderWindow::__init__()_

We need to find out a proper way to perform allocation and deallocation.

Rules
^^^^^

_Allocation rules_
- Never use ```__cinit__```, always use ```__init__```.
- In ```__init__```, never initialize a parent (no super())
- In ```__init__```, you always need to check if the local internal pointer is NULL before performing its allocation.
- In ```__init__```, just after the main allocation, update the internal pointer of all parents (you'll need to cast it).

_Deallocation rules_
- You need to make sure the parent's internal pointer is NULL.

_**Note:** just its parent, don't worry about grand-parents, etc. as it's a recursive mechanism: a parent will take care of its own parent._
- You need to delete your local internal pointer only if it's value isn't NULL.

No matter how complex an inheritance tree is, these simple rules will ensure a correct behavior.

Example
^^^^^^^

examples ::

    class Window:
        cdef sf.Window *p_window

        def __init__(self, args):
            if p_window == NULL:
                p_window = new sf.Window(*args)

        def __dealloc__(self):
            if p_window != NULL:
                del p_window

    class RenderWindow(Window):
        cdef sf.Window *p_renderwindow

        def __init__(self, args):
            if p_renderwindow == NULL:
                p_renderwindow = new sf.RenderWindow(*args)
                p_window = <sf.Window*>(p_renderwindow)

        def __dealloc__(self):
            p_window = NULL
            if p_renderwindow != NULL:
                del p_renderwindow


Explanations
^^^^^^^^^^^^
As we perform C allocation in ```__init__```, we need to anticipate the user code. He might call ```__init__(self, args)``` as much as he wants, that's why we check if the allocation already has been performed or not.

Each class is responsible for its own allocation and deallocation and give a hint to its parents so they can behave properly.

The first hint is to manually set the internal pointer of all parents, so they can know it doesn't need to allocate anything.

The second hint is to set the parent's internal pointer at NULL, so it can know it doesn't need to deallocate anything.
