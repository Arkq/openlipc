[open]lipc - open-source LIPC
=============================

LIPC seems to be an IPC library based on D-Bus. It links all Kindle components together. Via this
library one is able to expose application properties/settings, listen for or emit events, and many
more (potentially). It is considered to be one of the core components of the Kindle device.

This project is a reverse-engineered [header file](/include/openlipc.h) for this library. Since
the header file itself might be not enough, some auxiliary tools (e.g. lipc-get-prop, lipc-probe)
has been also reconstructed. They intend to be full replacements for the original ones (with few
modifications and enhancements).

For usage information consult the online [reference manual](https://arkq.github.io/openlipc/).


Installation
------------

	$ autoreconf --install
	$ ./configure --without-lipc-prop --without-lipc-probe
	$ make && make install

Or simply copy the header file into the system's include directory (e.g. /usr/include/).

If you want to compile exemplary tools as well, consider using steps as follows (assuming you are
performing cross-compilation, if not, omit all options for the configure step):

	$ autoreconf --install
	$ mkdir build && cd build
	$ export KINDLE_ROOTDIR=<absolute_patch_to_the_Kindle_root_directory>
	$ ../configure --enable-kindle-env --host=armv7a-softfp-linux-gnueabi
	$ make && make install


Acknowledgment
--------------

This project was inspired by the work of Bartek Fabiszewski, who has also reverse-engineered this
library. His [work](https://github.com/bfabiszewski/openlipc) was a starting point for my further
investigations.
