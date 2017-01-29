rf-bitbanger
============

Simple tools for experiments with bitbanged RF communication.

License: GPL v2. See the file COPYING for details.


Disclaimer
----------

Do not use the tools and code in situations where operation or lack of
operation may result in property damage, personal injury, or death.
Rules and regulations may control the use of RF communication at a
national level.  Do not use rf-bitbanger tools or code to break
applicable laws and regulations.


rfbb driver
-----------

LIRC style device driver that transmits and records pulse and
pause lengths using GPIO.  Uses code from `lirc_serial.c` by Ralph
Metzler et al.  See the file [HARDWARE.md][] for information on how to
connect the GPIO to a common 433 MHz TX module.

To build on target:

    cd rf-bitbanger/rfbb
    make KERNELDIR=~/linux
    sudo insmod rfbb.ko

Check for device node and add if not already there using dialout as
group:

    ls -al /dev/rfbb
    dmesg
    sudo mknod /dev/rfbb c 252 0
    sudo chown root:dialout /dev/rfbb
    sudo chmod g+rw /dev/rfbb


rfbb_cmd
--------

`rfbb_cmd` is a small tool, that acts as a remote control for switches
that use simple unidirectional communication based on OOK (On Off
Keying) modulation on a 433 MHz carrier.  `rfbb_cmd` uses the Linux
`rfbb.ko` kernel driver.

To build:

    cd rf-bitbanger/rfbb_cmd
    make
    sudo make install

A simple test on an old style (not selflearning) NEXA/PROVE/ARC set to
group D, channel 1.

    rfbb_cmd -d /dev/rfbb -i RFBB -p NEXA -g D -c 1 -l 1
    rfbb_cmd -d /dev/rfbb -i RFBB -p NEXA -g D -c 1 -l 0

Issue `rfbb_cmd --help` to get more information on supported protocols
and options.

**Note:** All protocols might not be fully tested due to lack of
receivers and time :)

rfcmd
-----

`rfcmd` is a another small tool that acts as a remote control for
switches that use simple unidirectional communication based on OOK (On
Off Keying) modulation on a 433 MHz.  `rfcmd` makes use of a
[tellstick](www.telldus.se) as transmitter instead of the `rfbb.ko`
kernel driver.

To build and test:

    cd rf-bitbanger/rfcmd
    make
    sudo make install
    rfcmd /dev/ttyUSB0 NEXA A 1 1
    rfcmd /dev/ttyUSB0 NEXA A 1 0 

Issue `rfcmd --help` to get more information on supported protocols and
options.

/Last update: 2012-07-03 Tord Andersson
