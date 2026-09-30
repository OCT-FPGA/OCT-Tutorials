# Xilinx License Setup Guide

Follow these steps to configure your license environment variable and verify connectivity to the Xilinx license server on the build machine.

## Prerequisites

* **Environment:** These commands must be run on an **OCT build machine** (where Xilinx tools including `vlm` are pre-configured in your system PATH).

## Step-by-Step Setup

### 1. Set the License Environment Variable

Set the `XILINXD_LICENSE_FILE` variable in your terminal session to point to the license server:

```
export XILINXD_LICENSE_FILE=2100@octlm
```

> **Tip:** To make this persistent across future terminal sessions on the build machine, you can add this line to your shell profile (e.g., `~/.bashrc`).

### 2. Verify License Accessibility

Launch the Vivado License Manager:

```
vlm
```

When the VLM graphical interface opens, check that Xilinx licenses are populated in the list. If so, close the VLM window to proceed to build.
