# eselect-opengl
Gentoo management module for switching OpenGL interface vendors. This a forked version of the Gentoo opengl.eselect module that currently supports switching between the Nvidia priorietary driver and the Mesa drivers.

ATI proprietary driver support could be added - but is currently not supported.

This implementation of OpenGL switching relies on isolating all GL implementations in subdirectories of a main ```/usr/lib{32,64}/opengl``` GL library directory. This avoids issues potentially arrising from the fact that Mesa and Nvidia GL libraries will be dynamically linked to _simultaneously_ in a Gentoo-based system (when using the in-tree *=app-eselect/eselect-opengl-1.3.1* package).

GL Switching is implemented by symbolically linking _all_ GL libraries for a particular GL implementation into the main system ```/usr/lib{32,64}``` library directories. Linker path overrides, specified in the OS environment, are _not_ used in this implementation of the opengl.eselect switching module. This makes a Gentoo System slightly more robust. Breakage is less likely to occur e.g. when using the native Steam client with the Nvidia proprietary drivers.

Some people might regard this module/script as a "retrogade" step... Especially since it is very similar to the implementation used in the older Gentoo versions of the *app-eselect/eselect-opengl* package (see version 1.2.7). They are wrong though :-)


