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

