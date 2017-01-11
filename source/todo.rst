TODO list
=========

While this is the first version of pySFML based on an *official* release of
SFML, it is still incomplete. While the bindings are *feature* complete, and
the external interface is stable (i.e. not likely to change), there is yet some
optimizations we can do to the implementation itself. Furthermore, the newly
introduced C/Cython API can be improved to make life easier for extension
authors.

Furthermore, some supplemental documentation such as tutorials and how-to guides are
incomplete, and we'd like to expand unit test coverage.

Please read further to see which action items are highest on our agenda.

Justifying the differences
^^^^^^^^^^^^^^^^^^^^^^^^^^
We want to provide a comprehensive list of all the differences between the
original API and these Python bindings API. As Python isn't C++, language
differences make it impossible to duplicate the C++ API in some  cases, and
impractical in others We'd like to provide a document justifying all these differences.



Enumeration
^^^^^^^^^^^
So far, a C++ enumeration is translated to a set of Python integer constants.
However, while porting Thor, we noticed some issues with this approach. A Thor
action (thor::Action) can be created from these enumerations but since they are
integer constants, we are unable to determine from which C++ enumeration they
came from; the type information has been lost.

Any solution to this will only affect the implementation and not the interface,
so users need not worry.



