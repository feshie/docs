# docs
overview of mountainsensing repos

To start from scratch:

Development packages:

sudo apt install protobuf-compiler python-protobuf gcc-arm-none-abi

mkdir feshie ; cd feshie

git clone --recursive https://github.com/feshie/contiki.git

git clone https://github.com/feshie/linux-gateway.git

in linux-gateway I needed this to pull protocol-buffers:

git submodule update --init --recursive

if you don't have msp430 compiler the border router only needs tunslip6 (normally built in make for rpl-border-router)

cd contiki/tools ; make tunslip6

BUILDING OUR CORE CODE
to program nodes (Muntjac):
  Connect USB cable to build PC
  Put node into bootloader mode by pressing USR and Reset at the same time, release Reset first
  Run " make TARGET=zoul BOARD=muntjac RADIO=cc1120 MOTES=/dev/ttyUSB0 z1-coap.upload " from mountainsensing/z1-coap
     N.B.: The serial port may vary depedning what else is plugged in. Look in /dev or try ttyUSB1 if USB0 doesn't work
     
to program nodes (Z1 + MS1):
  Connect usb cable to build PC
  Run " make TARGET=z1-feshie z1-coap.upload " from mountainsensing/z1-coap

There are typically MAKE shellscripts which do this in each major dir to avoid cold/battery/finger issues ;-)

z1-coap-config-defaults.h can be used to pre-configure the node

Normally 1200s interval 
