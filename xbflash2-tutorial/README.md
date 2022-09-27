# Flash program through PCIe bus for Alveo U280
This doc is used for demonstrating using [xbflash2](https://xilinx.github.io/XRT/2022.1/html/xbflash2.html). It is mainly from this xilinx [post](https://support.xilinx.com/s/article/Alveo-Updating-Vivado-images-via-PCIe-with-xbflash?language=en_US). The main purpose of this method is to enable users to program their Alveo cards through the PCIe bus. It requires a design that incorporates Xilinx AXI Quad-SPI core (flash controller). It also requires certain configurations and mapping to the PCIe BAR.

## Step 1: Check MCS on board

Get Xilinx device ID: 

`lspci -vd 10ee `

    3b:00.0 Processing accelerators: Xilinx Corporation Device d00c
        Subsystem: Xilinx Corporation Device 000e
        Flags: bus master, fast devsel, latency 0, IRQ 210, NUMA node 0
        Memory at ac000000 (64-bit, prefetchable) [size=32M]
        Memory at ae000000 (64-bit, prefetchable) [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: xclmgmt
        Kernel modules: xclmgmt

The device ID is `3b:00.0`

Use `xbmgmt` to check what image is running on the card:

`sudo xbmgmt examine -d 3b:00.0`

    ----------------------------------------
    1/1 [0000:3b:00.0] : xilinx_u280_GOLDEN
    ----------------------------------------
    Flash properties
      Type                 : spi
      Serial Number        : N/A
    
    Device properties
      Type                 : u280
      Name                 : N/A
      Config Mode          : 0
      Max Power            : N/A
    
    Flashable partitions running on FPGA
      Platform             : xilinx_u280_GOLDEN_8
      SC Version           : INACTIVE
      Platform ID          : N/A
    
    Flashable partitions installed in system
      Platform             : xilinx_u280_xdma_201920_3
      SC Version           : 4.3.10
      Platform ID          : 0x5e278820
    
    WARNING  : Device is not up-to-date.

If nothing is shown up, use Vivado flow with USB/JTAG to program the device with `./revert_to_golden.mcs`. Then reboot the machine and repeat step 1.

If the detected image is not golden image but other custom images, you could can run:

`sudo xbflash2 program --spi --revert-to-golden -d 3b:00.0 --bar-offset 0x40000`

NOTES: By default the bar offset for AXI-QSPI is set as 0x40000, it will be different for other design. Writing mcs to a wrong offset may cause kernel failure and system reboot. 

## Step 2: Program the device from golden image to openNIC shell.


The openNIC shell mcs is provided in this folder as `./openNIC_mt25qu.mcs`. 

Run

`sudo xbflash2 program --spi --image ./openNIC_mt25qu.mcs --bar-offset 0x40000 -d 3b:00.0`

    Preparing to program flash on device: 3b:00.0
    Are you sure you wish to proceed? [Y/n]: Y
    Successfully opened /dev/xfpga/flash.m15104.0
    flashing via QSPI driver
    Bitstream guard installed on flash @0x1002000
    Extracting bitstream from MCS data:
    .....................................
    Extracted 38190280 bytes from bitstream @0x1002000
    Writing bitstream to flash 0:
    .....................................
    Bitstream guard removed from flash
    ****************************************************
    Cold reboot machine to load the new image on device.
    ****************************************************

Then cold reboot the machine. 

Note: For golden image, the AXI-QSPI block is mapped to 0x40000 for Alveo U280. The bar offset will differ with different designs 

After reboot, you can load the opennic driver to check whether it is successfully loaded.

Or you can check the timestamp of this bitstream by using [pcimem](https://github.com/billfarrow/pcimem).

`sudo ./pcimem /sys/devices/pci0000:3a/0000:3a:00.0/0000:3b:00.0/resource2 0x0000` 

## Step 3: Revert to golden image
Run 

`sudo xbflash2 program --spi --revert-to-golden --bar 2 --bar-offset 0x80000 -d 3b:00.0`

    About to revert to golden image for device 3b:00.0
    Are you sure you wish to proceed? [Y/n]: Y
    flashing via QSPI controller located at 0x80000 on BAR2
    Successfully set bitstream guard!
    ****************************************************
    Cold reboot machine to load the new image on device.
    ****************************************************
After this, cold reboot the system. After reboot, you can check the image using xbmgmt mentioned in Step 1.