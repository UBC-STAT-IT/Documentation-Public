# DSI GPU Server Guide

# Table of Contents
1. [Introduction](#introduction)
    - [Server Related Commands](#server-related-commands)
2. [Conda Environment](#conda-environment)
3. [IDE (Integrated Development Environment)](#ide-integrated-development-environment)
    - [Running Python Code](#running-python-code)

## Introduction
For deep learning or computer vision workloads, it is usually advantageous to run them on systems that have access to a GPU (Graphical Processing Unit) as they excel in parallel operations and have high memory bandwidth.

A GPU server is available at the hostname `dsigpu.stat.ubc.ca` for exclusive use by DSSG fellows. 

Its current specifications are:

| Part | Info |
| ---- | ----------- |
| CPU | AMD Ryzen 9 5950X 16-Core Processor |  
| RAM | 64GB DDR4 | 
| GPU | Nvidia GeForce RTX 3050 |    
| CUDA | 12.1 |  
| Driver | 535.161.08 |
| OS | Ubuntu 20.04 |

Basic knowledge on using Linux through a terminal/console/command line is recommended.

### Server Related Commands
`nvidia-smi`: General information about the GPU (temperature, fan speed, memory usage, power usage, etc.)  
`nvcc --version`: Return CUDA toolkit version  
`top`: Show memory usage, CPU usage, and running processes  

To get a simple command line interface on the server, open a terminal or PowerShell window and use the SSH command:  
`ssh username@dsigpu.stat.ubc.ca`

To close the SSH session, enter the command `exit`.

It's recommended to write and run Python directly on the server to take full advantage of its capabilities.

For development related tasks (i.e. writing Python) using a command line interface is difficult, it's a good idea to use an IDE such as VSCode to interface with the server. This will be covered later in the document.

## Conda Environment

Before writing any code, we will need to setup a Python environment that will allow us to smoothly install and use packages as needed.

For this we will install `conda` which is a useful tool for Python package and environment managment.

First start an SSH session to dsigpu.stat.ubc.ca with the command `ssh username@dsigpu.stat.ubc.ca`.

Then enter the following commands in order on the server:
```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
~/miniconda3/bin/conda init bash
exit
```

The last `exit` command closes the SSH session to the server. Log back in with the SSH command from before.

The benefit of `conda` is that we can create environments which are isolated from eachother and each environment can have its own set of packages that can be used. Environments can also be deleted if needed without affecting other environments. This way you can easily experiment with packages in an environment, and if it breaks, just delete the environment and create a new one.

To create an environment use the command:  
```
conda create -n <env-name> python
```

`<env-name>` can be any descriptive name e.g. `torch-env`. The extra python argument at the end installs Python into the environment.

To list all available `conda` environments use the command:  
```
conda info --envs
```

Example output:
```
# conda environments:
#
base                  *  /zfs/users/asda9/asda9/miniconda3
demo                /zfs/users/asda9/asda9/miniconda3/envs/demo
```

The current environment we are in will have an asterisk to the right of its name. To start off with, we are put into a `conda` environment called `base` which should have no extra packages installed. 

**Do not** install anything to the `base` environment. Choose the `conda` environment to use from the list and "activate" it with the command:  
```
conda activate <env-name>
```

The current environment should be visible in the terminal beside our username, it should look similar to the following:
```
(demo) asda9@dsigpu:~$
```
Note the word `demo` in the parenthesis, this is the current `conda` environment the user is in.

Now that we have activated our new `conda` environment we can simply install packages with the usual commands `conda install` or `pip install`.

When installing packages that will use the GPU, ensure that they are compatible with the CUDA toolkit version installed on the server (currently 12.1).

To go back to the `base` environment use the command `conda activate`. 

To delete a `conda` environment use the command `conda env remove -n <env-name>`.

Whenever we log back in to `dsigpu.stat.ubc.ca` either through SSH or through VSCode, we will be placed into the `base` environment and will need to activate our chosen `conda` environment again.

## IDE (Integrated Development Environment)

It is best to use a user friendly coding environment on our own device like VSCode and connect it to `dsigpu.stat.ubc.ca` to write and run Python code on the server as well as to examine code output.

A general guide to connecting VSCode to a remove server can be found through this [link](https://www.digitalocean.com/community/tutorials/how-to-use-visual-studio-code-for-remote-development-via-the-remote-ssh-plugin).

Once connected to `dsigpu.stat.ubc.ca`, VSCode will show our home directory in its file navigation panel. Data and .py code files on the server can be created and accessed through this file navigation panel. 

We are also able to open a command line or console on the server through VSCode by going to the top menu bar and clicking **View->Terminal**. The keyboard shortcut is **Control+\`** on Mac or **Ctrl+\`** on windows (` is the backtick key on the top left of the keyboard under Esc).

In this console we will need to activate the `conda` environment we created earlier, `conda activate <env-name>`.

If while coding it's realized that a package is missing, we can install the package in the console like before with `conda install` or `pip install`.

Essentially any `conda` or other server commands from earlier will work in this VSCode console.

### Running Python code

To run Python code while in the VSCode console, navigate to the folder/directory containing the code with the Linux command `cd` and then run it with the command `python example.py` replacing example.py with the .py code file that should be run.