Hardware for the rfbb driver
============================
Latest update 2012-10-11, Tord Andersson

Note! A monospaced font might make it easier to read tables below!

RF Transmitter module pinout
----------------------------

A common RF transmitter module like TX433N (433.92MHz) has the following
pinout:

    Pin    Function
    ---------------
    1      GND
    2      Data in
    3      VCC
    4      Antenna

Make sure that VCC is able to operate from 5V DC and the Data In threshold 
is compatible with 3.3V logic.

The range is often 3 - 12 V DC, but there might be other versions!


Raspberry Pi example
--------------------

    RPI               TX433N
    -------------------------------------------------------------
    Pin, function  -  Pin, function
    P1-02, 5V0     -  3, VCC
    P1-06, GND     -  1, GND
    P1-11, GPIO17  -  2, Data in
    No connection  -  4, Antenna. Connect a 170mm wire as antenna 

