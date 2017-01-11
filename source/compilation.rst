Compilation
===========
Python can be run with various configuration, on various platforms with
hetergenous environments. It involves various concepts such as
libraries, environemnt variables, compilers. Let me say
it straight, it's *NOT* easy. Although this document is nice with you ,
you're expected to know your stuff. If anything goes wrong, even a minor
problem can become a overhelming.

Now that you're warned, let's continue.

Getting the source code
-----------------------
Before attempting to compile, it is important that you obtain a copy of
the source code, either from git. ::

    git clone http://github.com/Sonkun/python-sfml
    cd python-sfml

You can also download a specific version by speficying the tag. You can
request the available tags with `git l tags`. ::

    git clone --branch v2.3.2 http://github.com/Sonkun/python-sfml

The secound thing you've got to do is installing the requirements which
are Cython and SFML. You should be fine with the latest version of Cython
(was tested with 0.24) however, the SFML version must match exactly the
version of these bindings. In case you want to build the development
branch, use the development branch of SFML.

Backgrond
---------
If making these bindings working was the only goal, it wouldn't be that
painless.
Besides getting a working system, one must be able to extend by writing
extensions (requires the C API installed), to embed in or simply
distribute.
Compiling and installing these bindings must adress these issues.
So before we step in with the actual compilation, let's have a look at
the background.

Understanding the concept of Python environement can help, especially
when there can be many Python version installed on one system. We can
distinguish two kinds of Python install which is system wide, or not.

On Windows, no concept like this, one directory, everything self-contained

On Mac OS X, concept of framework,

On Linux,



Sure, Windows, Mac OS X, Linux comes with differences and
we need to be accustomed to each of these platforms.


the ability to compile other extension afteder
Yet, these things will depend on the underlying operating system and
whether system wide or not

Python runs for various platforms, in various environements, various version
you can compile static, dynamically
system wide or not
pyenv or not
and it can easily leads to multiple

Background
- need to compile other extension based
- see Python dir as a self contained env
- system-wide

LATER
-----
two use cases:
- I want to embed (gamestutra) (need of pySFML headers)
- I want to extend (pyThor)
- I want to distribute (concern: dll bundled ?)

Linux and Mac OSX
^^^^^^^^^^^^^^^^^
In order to compile, you'll need the Python development files.

To build the bindings for Python, type::

   python2 setup.py install
   python3 setup.py install

Windows
^^^^^^^
Compiling on Windows requires more steps.

To have binaries fully compatible you should compile with the optimizing
C/C++ compiler used to build Python for Windows. The SDK can be
downloaded on the Microsoft download center:

For Python 2.7 until 3.2: `Windows SDK 7.0 <http://www.microsoft.com/en-us/download/details.aspx?id=18950>`_

For Python 3.3 and later: `Windows SDK 7.1 <http://www.microsoft.com/en-us/download/details.aspx?id=8442>`_

.. note::

   If you planned to compile for both version (and thus install both SDKs (7.0 and 7.1),
   dont't install redistributable packages otherwise you'll run accross an installation
   failure when installing the second SDK. To do that, uncheck "Microsoft Visual C++ 2010"
   case.

You need **GRMSDKX_EN_DVD.iso** if you target a **AMD64** Python version. It
can build for x86 arch too.

Observe that you don't need Microsoft Visual C++ Express.

Open the SDK command window and type::

	C:\Program Files\Microsoft SDKs\Windows\v7.0>set DISTUTILS_USE_SDK=1
	C:\Program Files\Microsoft SDKs\Windows\v7.0>setenv /x64 /release

Adjust according the targeted architecture (x86 or x84) and mode (release or debug).

Then head to the source directory and type::

    python setup.py install

It you want to create an installer, simply type::

	python setup.py bdist_msi

.. _SFML: http://python-sfml.org/downloads/sfml-2.1.0.tar.gz
.. _cython: http://cython.org
