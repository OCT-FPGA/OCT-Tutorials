# Issues and Fixes

**Issue**

When trying to build the software application, you may get the following error.

```bash
fatal error: CL/cl2.hpp: No such file or directory
```
**Fix**

Install OpenCL headers by running ```sudo apt install opencl-headers``` and then re-run the build command.

**Issue**

You get the following warning when trying to clone a repository.

Basic authentication using a password to Git is deprecated and will soon no longer work. Visit https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information around suggested workarounds and removal dates."

**Fix**

Follow the instructions in [this page](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) to generate a personal access token. The generated token can be used as the password. However it's not easy to remember the token like a password. So it is convenient for you to store this token in the MOC machine so you won't have to re-enter it every time you try to clone a repository. To do this run this command.

```bash
git config --global credential.helper store
```
Then clone the repository. Remember to use the token when asked for the password. You will only have to do this once. The credentials you enter get stored in the credential store, and next time you clone a repository, it's not required to enter the user name and password.
