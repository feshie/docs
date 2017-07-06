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

to program nodes:

make TARGET=zoul BOARD=muntjac RADIO=cc1120 MOTES=/dev/ttyUSB0 z1-coap.upload

There are typically MAKE shellscripts which do this in each major dir to avoid cold/battery/finger issues ;-)

z1-coap-config-defaults.h can be used to pre-configure the node

Normally 1200s interval 
