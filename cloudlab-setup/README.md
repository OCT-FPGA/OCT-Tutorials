# CloudLab U280 FPGA Experiment Setup

The CloudLab Umass cluster has 8 nodes, each of which hosts an Alveo U280 FPGA accelerator card. You need to create a CloudLab experiment to access any of these FPGAs. An experiment will give you access to a bare-metal node. By using an experiment profile, you can configure this node so that it will have the tools required to access the FPGA.  If you are not familiar with the CloudLab experiment workflow, it is strongly recommended to refer to [The CloudLab Manual](http://docs.cloudlab.us/) before getting started.

## 1. Set up a Cloudlab project

If you already have a CloudLab account, skip to Section 1.2.

### 1.1 New users

Go to [cloudlab.us](https://cloudlab.us) and click Request an Account.

![plot](images/new_account_1.png)

Enter your details. You need to provide an SSH public key. Make sure you have access to the corresponding private key which you will need to log in to the Cloudlab server. For specific instructions on how to create a key-pair and access your CloudLab node using either MOC or your home/work computer, please refer to [this tutorial](https://github.com/OCT-FPGA/OCT-Tutorials/blob/master/managing-keys/setup-keys.md). Select Join Existing Project, enter ```OCTFPGA``` and submit the request.

![plot](images/new_account_2.png)

The account approval process could take a couple of days. Once you got the approval, go to step 2. 

### 1.2. Existing users

If you already have a Cloudlab account, first log into your account and select Start/Join Project. 

![plot](images/existing-account_1.png)

Enter the project name ```OCTFPGA``` and click Submit Request.

![plot](images/existing-account_2.png)

As an existing user, you should already have a key-pair which you need to remotely access a CloudLab node. If you need to upload a different public key, you may do so by going to "your user name" &#8594; Manage SSH Keys, 
  
![plot](images/existing-account_3.png)
  
and entering your public key. Steps on how to create an SSH key-pair can be found [here](https://github.com/OCT-FPGA/oct-tutorials/blob/main/managing-keys/setup-keys.md).

![plot](images/existing-account_4.png)


## 2. Start an experiment

Now you need to select or create an experiment profile. For FPGA experiments, we have created the profile ```fpga-post-boot``` for your reference. This profile can be used to boot up either an Ubuntu or CentOS image and install run-time tools automatically by running a post-boot script in the background. It is also possible to create your own profiles. To learn how to do this, please refer to [The Cloudlab Manual](http://docs.cloudlab.us/).

Select Experiments &#8594; Start Experiment.

![plot](images/experiment_1.png)

Click Change Profile and select the profile ```fpga-post-boot```.

![plot](images/post-boot-0.png)

Click Next.

![plot](images/post-boot-1.png)

You can customize the experiment by parameterizing the setup. Enter the number of nodes, a tool version, and an OS from the available list of options. In this tutorial we use 1 node. The tool version is 2020.1.1 and the OS is Ubuntu 18.04. 

![plot](images/post-boot-2.png)

Optionally enter a name for the experiment and click Next.

![plot](images/post-boot-3.png)

You can set the experiment duration now, or click Finish. The default is 16 hours. It is important to keep in mind that after 16 hours, everything you have done in this experiment will be wiped out from your node. Therefore, ensure that you complete the experiment by then and save the experiment outputs in a persistent storage.

![plot](images/experiment_6.png)

Now, CloudLab will start provisioning cloud resources based on the parameters you specified. 

![plot](images/post-boot-4.png)

Now the Cloudlab node will start to boot up.

![plot](images/post-boot-5.png)

![plot](images/post-boot-6.png)

![plot](images/post-boot-7.png)

![plot](images/post-boot-8.png)

Switch to the tab List View. Now you will see the SSH command that you can use to conect to this server. 


![plot](images/post-boot-9.png)

Use any SSH client (along with your private key) to connect to the Cloudlab node you just created. FPGA binaries and host executables can be created by running tools on MOC. You can copy these files from the MOC VM and execute them in your Coudlab node now. 

## Useful links

[The CloudLab Manual](http://docs.cloudlab.us/)
