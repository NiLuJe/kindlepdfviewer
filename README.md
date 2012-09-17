kpdfdjview
==========

kpdfdjview is a PDF and DjVu viewer application, created for the Kindle e-Ink readers.
It is currently restricted to 4bpp inverse grayscale displays and runs on
Kindle 3 and Kindle DXG devices.
It is using the muPDF library (see http://mupdf.com/) and its UI is scripted
in Lua (see http://www.lua.org/).

The application is licensed under the GPLv3 (see COPYING file).


Building
========

Follow these steps:

* run `make fetchthirdparty`
* run `make thirdparty`
* run `make`


Running
=======

The user interface (or what's there yet) is scripted in Lua. See "reader.lua".
It uses the Linux feature to run scripts by using a corresponding line at its
start.
So you might just call that script. Note that the script and the kpdfdjview
binary currently must be in the same directory.
You would then just call reader.lua, giving the document file path as its first
argument. Run reader.lua without arguments to see usage notes.
The reader.lua script can also show a file chooser: it will do this when you
call it with a directory (instead of a file) as first argument.


Device emulation
================

The code also features a device emulation. You need SDL headers and library
for this. It allows to develop on a standard PC and saves precious development
time. It might also compose the most unfriendly desktop PDF reader, depending
on your view.

To build in "emulation mode", you need to run make like this:

```
make clean cleanthirdparty
EMULATE_READER=1 make thirdparty kpdfdjview
```

And run the emulator like this:
```
./reader.lua /PATH/TO/PDF.pdf
```

By default emulation will provide DXG resolution of 824*1200. It can be
specified at compile time, this is example for Kindle 3:

```
EMULATE_READER_W=600 EMULATE_READER_H=800 EMULATE_READER=1 make kpdfdjview
```
