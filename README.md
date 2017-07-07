# Docs
Overview of how to build firmware for the Mountainsensing nodes. See mountainsensing.org

## To start from scratch:

### Development packages:
To get the code for building nodes and running a Linux gateway, run:
* sudo apt install protobuf-compiler python-protobuf gcc-arm-none-abi
* mkdir feshie ; cd feshie
* git clone --recursive https://github.com/feshie/contiki.git
* git clone https://github.com/feshie/linux-gateway.git
* cd contiki; git submodule update --init --recursive
* cd ../
* cd linux-gateway; git submodule update --init --recursive

If you want to build msp430-based nodes you will need msp430gcc - either install the package or use the Instant Contiki VM.

if you don't have msp430 compiler the border router only needs tunslip6 (normally built in make for rpl-border-router)
* cd contiki/tools ; make tunslip6

## BUILDING OUR CORE CODE

to program nodes (Muntjac):

* Connect USB cable to build PC
* Put node into bootloader mode by pressing USR and Reset at the same time, release Reset first
* Run " make TARGET=zoul BOARD=muntjac RADIO=cc1120 MOTES=/dev/ttyUSB0 z1-coap.upload " from mountainsensing/z1-coap
     N.B.: The serial port may vary depedning what else is plugged in. Look in /dev or try ttyUSB1 if USB0 doesn't work
     
to program nodes (Z1 + MS1):

* Connect usb cable to build PC
* Run " make TARGET=z1-feshie z1-coap.upload " from mountainsensing/z1-coap

There are typically MAKE shellscripts which do this for muntjac/ms2s in each major dir to avoid cold/battery/finger issues ;-)

z1-coap-config-defaults.h can be used to pre-configure the node. Note power boards are all id 22

Normally 1200s interval 

## Miscellaneous
The z1-nothing / remote-nothing projects can be used to just test networking or as a basis for running other tests/experiments that don't need our code. -nothing nodes can also be used as routing nodes with no sensors. These are built in the same way as z1-coap but with z1-nothing.upload or remote-nothing.upload instead of z1-coap.upload.

## Border Router

ipv6 prefix is set in the border-router script

## Fetcher

The Java CoAP data fetcher/configurer has the IPv6 prefix stored in common.conf and a list of node 4byte endings in nodes.conf

checking config - make sure you use the correct prefix:

java -jar fetcher.jar -p 2001:630:d0:f308: get-config 9e48

--help lists everything including get-date and set-date

