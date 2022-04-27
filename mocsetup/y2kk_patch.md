# Applying the Patch for Xilinx Revision Number Overflow Issue (Y2K22)

The revision number overflow issue may cause build errors when trying to export certain IPs. Xilinx has created a [patch](https://support.xilinx.com/s/article/76960) which should be downloaded and installed in order to overcome this issue.

## Steps

Download the patch from the above link.

Extract the patch to /tools/Xilinx (i.e., after extracting, the path of the patch should be /tools/Xilinx/y2kk_patch)

Change the directory to `/tools/Xilinx`

Run the following command:

`sudo python3.6 y2k22_patch/patch.py`

If successfully patched, you should see a list of messages similar to the following:


[2022-02-14] INFO: This script (version: 1.2) patches Xilinx Tools for HLS Y2k22 bug for the following release: 
2014.*, 2015.*, 2016.*, 2017.*, 2018.*, 2019.*, 2020.* and 2021.*

[2022-02-14] UPDATE: /tools/Xilinx/Vivado/2020.1/common/scripts

[2022-02-14] COPY: /tools/Xilinx/y2k22_patch/automg_patch_20220104.tcl  to /tools/Xilinx/Vivado/2020.1/common/scripts/automg_patch_20220104.tcl 

[2022-02-14] UPDATE: /tools/Xilinx/Vitis/2020.1/common/scripts

[2022-02-14] COPY: /tools/Xilinx/y2k22_patch/automg_patch_20220104.tcl  to /tools/Xilinx/Vitis/2020.1/common/scripts/automg_patch_20220104.tcl 

