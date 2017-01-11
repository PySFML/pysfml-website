Remaining tasks
===============
We're about to release version 2.3.2 of these bindings and they come with
many improvements.

.. TODO: maybe later implement buffer protocol for image that retains
.. the number of dimension, we wouldn't have to pass the width and height
.. when creating from "pixels"
.. image = sf.Image.from_pixels(width, height, bytes())

General
-------
* Review and rewrite event system (Urgent!)
* Add to pipy
* compile pyThor and add to pipi
* implement buffer protocol
* remove character glitch
* dealing with strings/bytes/unicode coercion better
* Remove import__module__name() in C++ code
* correct English documentation

System
------
*  Implement sf.InputStream and from_stream methods #27

Graphics
--------
* sf.Text constructor (I remember it was a mess when implementing this constructor)
* Improve sf.Text.string #43 (implementing the encode/decode step properly)

Network
-------
* [2.4] Review the entire module
* SocketSelector, Ftp and Http still need to be implemented
* Make sf.Socket derivable #48 (Derived sockets seems to have access to protected functions such getHandle(), create(), etc it may override.)
* Improve socket design (There's an issue with non-blocking socket. Implementing status as exceptions screw this socket mode.)
* Implement sf.Packet #26


Packaging
---------
* Automate packaging

Documentation
-------------
* [2.3] translate original tutorials (from C++ to Python)
* Lack of information about operator in the documentation
* Add information about copyable classes to the documentation (How do people find out if one object is copyable via the copy module or not ?)
* Add documentation for Ftp, Http, SocketSelector and HandledWindow #50

Examples
--------
* Review all examples
* Improve Sound example("\rPlaying... " << std::fixed << std::setprecision(2) << sound.GetPlayingOffset()) #32

Website
-------
* Finish website
