# docs
overview of mountainsensing repos

To start from scratch:

mkdir mountainsensing ; cd mountainsensing

git clone --recursive https://github.com/feshie/contiki.git

git clone https://github.com/feshie/linux-gateway.git

in linux-gateway I needed this to pull protocol-buffers:

git submodule update --init --recursive



cd contiki/tools ; make tunslip6

