# Getting Started

The Open Cloud Testbed (OCT) workflow consists of two parts.

**1. Development:** 
OCT development tools are available on build machines that can be allocated as virtual machines (VMs) within a CloudLab experiment. Users can remotely log in to these VMs to build FPGA bitstreams and host executables.

**2. Deployment:**
After creating the bitstreams/host executables, users will use CloudLab for targeting. OCT currently consists of 24 AMD Alveo U280s, 4 AMD VCK5000s, 4 AMD V70s, and 2 NVIDIA V100 GPUs. The U280s and VCK5000s are connected to 100 GbE data center switches using QSFP28 passive DAC cables. 

![plot](images/oct-arch.jpg)

The table below shows the hardware available in OCT along with the host nodes.

| Hardware | Nodes          |
|----------|----------------|
| U280     | pc151-pc175    |
| VCK5000  | pc176-pc179    |
| V70      | pc180-pc183    |
| V100     | pc178-pc179    |

All nodes are equipped with 40 GbE regular NICs. In addition, pc160–pc163 also have 100 GbE NICs for high-bandwidth networking.

We have created the CloudLab profiles ```oct-u280```, ```oct-vck5000```, and ```oct-v70``` to help users select nodes with the specific resources they need. 

## Requesting Accounts

[Requesting Access to OCT](https://github.com/OCT-FPGA/OCT-Tutorials/blob/master/cloudlab-setup/accounts.md)

## Getting Started with Build Machines

[Allocating a Build Machine in OCT](https://github.com/OCT-FPGA/OCT-Tutorials/blob/master/cloudlab-setup/build-machines.md)

## Getting Started with FPGAs

[Getting Started with FPGAs in OCT](https://github.com/OCT-FPGA/OCT-Tutorials/blob/master/cloudlab-setup/fpgas.md)

## U280 Tutorials

[Vector Addition](https://github.com/OCT-FPGA/Vitis-Tutorials-U280/tree/2022.2/VitisAccelHelloWorld)

[UDP Network Demo](https://github.com/OCT-FPGA/udp-network-demo)

## Versal Tutorials (VCK5000 and V70)

[Getting Started with V70s](https://github.com/OCT-FPGA/versal-tutorials/blob/main/v70-getting-started.md)

[Getting started with VCK5000s](https://github.com/OCT-FPGA/versal-tutorials/blob/main/vck5000-getting-started.md)
