============
vmod_dgram
============

----------------------
Varnish UDP Dgram Module
----------------------

:Author: Matthew M. Boedicker
:Author: Maksim Naumov
:Modified by: didebuli
:Date: 2021-07-19
:Version: 6.5.2
:Manual section: 3

notice
------

I'm not a professional developer, but I did need this module to work with newer Varnish versions.
This is the result... it should work with Varnish 6.5 .
Use this module on your own risk.


SYNOPSIS
========

import dgram;

sub vcl_deliver {
  dgram.send(req.request + " " + req.http.host + req.url, "127.0.0.1", 12345);
}

DESCRIPTION
===========

Varnish module to send arbitrary data over UDP from VCL.

The original use case is a hit counter that will send the URL served for
every request to a simple UDP server for further processing.

FUNCTIONS
=========

dgram
-----

Prototype
        ::

                send(STRING S, STRING HOST, INT PORT)
Return value
	VOID
Description
        Sends S as UDP to HOST:PORT.
Example
        ::

                dgram.send("Hello world", "127.0.0.1", 12345);

INSTALLATION
============

If you received this package without a pre-generated configure script, you must
have the GNU Autotools installed, and can then run the 'autogen.sh' script. If
you received this package with a configure script, skip to the second
command-line under Usage to configure.

Usage::

 # Generate configure script
 ./autogen.sh

 # Execute configure script
 ./configure [PKG_CONFIG=PATH]

Make targets:

* make - builds the vmod
* make install - installs your vmod
* make check - runs the unit tests in ``src/tests/*.vtc``

HISTORY
=======

COPYRIGHT
=========

* Copyright (c) 2013 Matthew M. Boedicker
* Copyright (c) 2015 Maksim Naumov
