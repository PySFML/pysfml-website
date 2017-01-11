Documents
=========
While people are encouraged to port parts of their
game (or the totalliy) to Python, writing SFML. Even though when I
started this project a 5 years ago I was still a beginner, it took
me countless rewrite or readjustement to obtain a satisfiying bindings.
While my journey was long, I can shorten the other peoples journey by
sharing the knowledge I've gained.

I knew several things before I started it.

Languages with all their programming idioms are complicated enough.
When porting a SFML based library to Python, decisions must be taken based
on them. A strong exerperience in both language as well as in the library
is needed to port properly.

3 main documents
* mapping properly (fundamental differences between Python and C++)
* how to deal with a, b,c
* convention used
* justifying implementation




other




.. rubric:: Footnotes

.. [#] For example, we provide bindings for SFML's network module. Even
       Though such functionality can be found in Python's socket module, we
       believe that its inclusion not only aids developers as they
       port their software from C++ to Python or vice-versa, but we also find
       SFML's API more convenient in some cases (e.g. when obtaining a public IP
       address).


Fundamental differences + proper mapping
----------------------------------------
Abc.

Alternative to multiple definition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

but we have default and positional arguments
we usually define multiple class constructor


@classmethod

construct_from_x(x)
construct_from_y(y)


Force a set of positional arguments

.. def function(pixels, *args):
..     if not args:
..         pass # do something
..     else:
..         x, y, z = args
..         pass # do something else

common idio to_something()
^^^^^^^^^^^^^^^^^^^^^^^^^^
todo: explain

No pointer
^^^^^^^^^^
A common idiom in C/C++ is to pass a pointer that caller has to

.. void function(int* size)
.. {
..     *size = actual_size;
.. }

How to deal with...
-------------------

Unicode, Bytes, String, etc
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Abc

Memory view
^^^^^^^^^^^
Abc
