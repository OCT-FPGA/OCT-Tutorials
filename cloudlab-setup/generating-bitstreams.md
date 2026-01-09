# Getting started with building P4 bitstreams on OCT

Some initial setup is required on OCT machines before building bitstreams as mentioned in [P4Framework](https://github.com/OCT-FPGA/P4Framework/tree/master).


## Verify vitis_net ip

Run `ls -d /share/Xilinx/Vivado/2023.1/data/ip/xilinx/vitis_net_p4* 2>/dev/null` 

This should output something like:

`/share/Xilinx/Vivado/2023.1/data/ip/xilinx/vitis_net_p4_v1_3` indicating VitisNetIP is present for the Vivado version 2023.1.

## Setup Vivado environment

Run `source /share/Xilinx/Vivado/2023.1/settings64.sh` 

Verify Vivado version 2023.1.

`which vivado`

`vivado -version | head`

## Update the license 

Run `export XILINXD_LICENSE_FILE=2100@xilinxlm` 

## Verify that the Makefile in P4Framework has the right Vivado version:

`VIVADO_TARGET_VER=2023.1`

Now the steps mentioned in [P4Framework](https://github.com/OCT-FPGA/P4Framework/tree/master) can be followed to build P4 bitstreams.
