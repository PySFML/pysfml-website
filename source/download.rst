Download
========
Since version 2.3.2, these bindings were added to PyPI (the Python
Package Index repository) and it really should be the way you install
SFML. However, there are some exceptions, or special use cases to
consider, so let's check them together.

To compile, check this document :doc:`compilation`.

The PyPI repository
-------------------
Unless you run a distribution of Linux, PyPI will be your choice number
one. Typing the following command should suffice on most operating
system. ::

    pip install pysfml

Check the documentation of the PyPI project because they are numerous
options you can do such as installing a specific version.

.. warning ::

    On Linux, make sure you uninstalled any system-wide installed version
    of pySFML before using pip. For instance, you have to type "apt-get
    remove python-sfml" on Ubuntu.

If installing this through *pip* fails (but it shouldn't so please,
report), fall back on the following options.

Windows
-------
On Windows, as an alternative to PyPI, you could also use the following
installers. According to your Python version (and the architecture),
choose one below and follow the instructions.

.. note::

    If you experience issues during installation, try running the installer
    again in compatibility mode:

        1. Right-click the installer and select "Properties"
        2. Navigate to the "Compatibility" tab.
        3. Check "Run this program in compatibility mode for"
        4. Select "Windows XP (Service Pack 3)

* `pySFML-2.3.2.win32-py2.7.exe <http://python-sfml.org/downloads/2.3.2/pySFML-2.1.0.win32-py2.7.exe>`_ [Python 2.7] [32 bit]
* `pySFML-2.3.2.win32-py3.5.exe <http://python-sfml.org/downloads/2.3.2/pySFML-2.1.0.win32-py3.4.exe>`_ [Python 3.5] [32 bit]
* `pySFML-2.3.2.win64-py2.7.exe <http://python-sfml.org/downloads/2.3.2/pySFML-2.1.0.win64-py2.7.exe>`_ [Python 2.7] [64 bit]
* `pySFML-2.3.2.win64-py3.5.exe <http://python-sfml.org/downloads/2.3.2/pySFML-2.1.0.win64-py3.4.exe>`_ [Python 3.5] [64 bit]

This should work on any recent version of Windows. Don't forget that
support for Windows XP was dropped in Python 3.5.

Mac OSX
-------
While official support for Mac OSX is slated for the next release, those eager
should feel free to download the source code and compile manually.

For example, through pip (don't forget to have cython 0.20 and SFML 2.1
installed and as mentioned below): ::

   pip install git+git://github.com/Sonkun/python-sfml.git

Ubuntu
------
This is available in the official repository and installing should be a
matter of. ::

    apt-get install python-sfml

However, according to the version, you . This is because only security update after a distribution is out.
Alternatively, you may want to check :doc:`repositories`.

Fedora
------
This is also  ::

    yum install python-sfml
