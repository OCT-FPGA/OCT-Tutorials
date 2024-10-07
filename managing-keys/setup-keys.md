# Create SSH Keys for Remote Access

## Steps

Open a terminal and enter the following command.

```bash
$ssh-keygen
``` 

Enter a name and location for the SSH key that you will create. Optionally enter a key passphrase for added security.

![plot](images/key-generation.png)

You will have two keys; a public key and a private key. The public key ends with the extension .pub. If you want to access a CloudLab node, this key needs to be copied before you start your CloudLab experiment. Check [this](https://github.com/OCT-FPGA/oct-tutorials/tree/master/cloudlab-setup#12-existing-users) for details on how this is done.  
