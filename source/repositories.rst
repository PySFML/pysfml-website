Repositories
============

Ubuntu
------

Packages are available for Ubuntu starting from 14.04 or greater via launchpad::

   sudo add-apt-repository ppa:sfml/stable
   sudo apt-get update
   sudo apt-get install python-sfml
   # or
   sudo apt-get install python3-sfml

Want the development version to benefit the latest bug fixes or features ?
Use `ppa:sfml/development` repository, daily builds are available.

.. note::
   These repositories provide many packages. The library SFML
   and the bindings are included along with their examples. Packages are:

      * libsfml
      * libsfml-dev
      * libsfml-dbg
      * libsfml-doc
      * sfml-examples

      * python-sfml
      * python3-sfml
      * python-sfml-doc
      * pysfml-examples

   Once example packages are installed you may want to launch them to
   see if the library works well with your graphics card. To do that
   just run the following commands. ::

      sfml-sound # will run the example 'sound'
      sfml-shader
      sfml-X11
      sfml-voip

      pysfml-sound # will run the same example but it's actually a python script that uses the binding
      pysfml-pong
      pysfml-sockets
      pysfml-spacial-music
      pysfml-pyqt4

Fedora
------
todo
