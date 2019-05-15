			IAS	Wayland compositor
			======================

IAS stands for Intel Automotive Solution compositor for Wayland(R). 
As the name suggests, it is a Wayland compositor for automotive
specific segment. The main idea behind IAS is to show case Intel's
GPU and display controller capabilties.
Open source Weston has 4 major components. The shell, the core, the
backend and the renderer. IAS' goal is to reuse as much of Weston as
possible, so we strive to keep the core and renderer as close to
open source Weston as possible. The shell was rewritten for automotive
needs and is called IAS shell. Same thing is true for the backend which
tries to utilize HW capabilities found on Intel SoCs.
While there are many capabilities unique to IAS, some of the salient ones
include  surface sharing between multiple virtual machines as well as
remote display which allows for surface sharing between multiple SoCs.

Building IAS:
-----------

The following build options should be used to compile IAS:
./autogen.sh --disable-setuid-install \
        --enable-ias-shell \
        --disable-xkbcommon \
        --enable-simple-clients \
        --enable-clients \
        --disable-wayland-compositor \
        --disable-libunwind \
        --disable-xwayland \
        --disable-xwayland-test \
        --disable-x11-compositor \
        --disable-rpi-compositor \
        --enable-ivi-plugin-manager \
        --enable-layer-manager-control \
        --disable-tracing \
        --enable-shadergen 

For a complete list of flags that you can provide with 
autogen.sh, please go to IAS folder and run:
./configure --help

After the successful completion of the above autogen.sh step:
make -j <number of cores that you want to use>
make install
