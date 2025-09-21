# Allocating a Build Machine in OCT

This guide explains how to allocate a build machine in OCT. These build machines are preconfigured with **Xilinx Vitis** and **Vivado**, so you can compile and build FPGA projects without needing to install the tools yourself.  

Use the profile `oct-build` to spin up a build machine.
![plot](images/bm-1.png)
Click Next.
![plot](images/bm-2.png)

For the VM, choose the RAM, number of vCPUs, and the tool version. If you want to use VNC, enable the remote desktop option, and click Next.
![plot](images/bm-3.png)

Enter a name for the experiment (optional), then click Next.
![plot](images/bm-4.png)

When you click Finish, the CloudLab experiment will start.
![plot](images/bm-5.png)

CloudLab starts provisioning your experiment. This means that CloudLab is reserving the hardware you requested, loading the correct images, and applying your chosen settings (like RAM, vCPUs, and so on).
![plot](images/bm-6.png)

After that, the node will boot up.
![plot](images/bm-7.png)


![plot](images/bm-8.png)

After the node finishes booting, the startup services will launch. This installs all the tools you need, including Xilinx Runtime and others required to build bitstreams, as well as any components needed for VNC access if you selected the remote desktop option when setting up the experiment. Do not log into the node while the startup services are still running, as the setup is not complete.
![plot](images/bm-9.png)

Once the startup services are complete, a checkmark will appear on the node icon. After that, you can log into the node. You’ll also see the SSH command you need to use to access it.
![plot](images/bm-10.png)


![plot](images/bm-11.png)

Add this information to your `~/.ssh/config` file.

```
Host oct-build
    HostName <host name>
    User <user name>
    Port <port>
    IdentityFile <private key>
    LocalForward 5901 localhost:5901
```

Replace `<host name>`, `<username>`, `<port>`, and `<private key>` with your own details. This setup also forwards port 5901 so you can use VNC if needed.

After updating your `~/.ssh/config`, connect to the build machine by running `ssh oct-build`.

On the build machine, run the following command to start a VNC server instance (only if you selected remote desktop access when setting up the experiment).

`vncserver -localhost no -geometry 1920x1080`

You can set your preferred resolution by replacing 1920x1080 with your desired width and height when running the VNC server command.

![plot](images/bm-12.png)

Use any VNC client, such as [RealVNC](https://www.realvnc.com), to connect to the VNC server.

Open the VNC Viewer, and goto File &#8594; New connection... to create a new connection.

![plot](images/mac_vnc1.png)

Enter a name for your VNC connection.
![plot](images/mac_vnc2.png)

To access the connection properties, right-click the connection icon and then click Properties.
![plot](images/mac_vnc3.png)


![plot](images/bm-13.png)


![plot](images/bm-14.png)


![plot](images/bm-15.png)
