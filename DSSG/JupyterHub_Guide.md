# DSSG JupyterHub Guide

# Table of Contents
1. [Introduction](#introduction)
2. [Logging in](#logging-in)
3. [Navigation](#navigation)
4. [Create a notebook](#creating-a-notebook)
5. [Opening a Terminal window](#opening-a-terminal-window)
6. [Installing packages](#installing-packages)
7. [Logging out](#logging-out)
8. [Troubleshooting](#troubleshooting)

## Introduction

JupyterHub is a service provided by the UBC Statistics Department that allows you to use JupyterLab from the browser without having to configure JupyterLab on your own device. JupyterHub uses Docker containers in the backend to enable this. 

The DSSG JupyterHub is located at the link https://r9-dssg.stat.ubc.ca.

If you prefer RStudio there is a large clickable icon on the home page that takes you to an instance of RStudio. Your login information (username and password) will be the same for both RStudio and JupyterHub.

JupyterHub and RStudio are used for R or Python workloads that don't require a GPU. If you absolutely require a GPU for deep learning or computer vision, then you will need to use the DSI GPU server instead. The guide for the GPU server is located [here](https://github.com/UBC-STAT-IT/Documentation-Public/blob/main/DSSG/DSIGPU_Server_Guide.md). It will accept the same username and password. 

## Logging in

One of the ASDa accounts (asda1,asda2,...) will be assigned to you. This account will grant access to JupyterHub, RStudio, and the DSI GPU server. 

You will also be asked to create a password for your account. Create a password hash [here](https://r9e-web.stat.ubc.ca/sha512-password-hash-generator) and send it back to the requestor so the IT admin can set the password.

Once your password is set, go to the [DSSG JupyterHub](https://r9-dssg.stat.ubc.ca) with a browser such as Chrome or Edge and click the house icon under `Sign in with your account`.

## Navigation

Once logged in you will be shown a JupyterLab environment. If you haven't used JupyterLab before, an in depth guide is located [here](https://jupyterlab.readthedocs.io/en/stable/user/interface.html).

The file system panel on the left will show your home directory. This is where you will work on files only accessible by you. To share your work with your teammates and the DSI teaching team, you will use the designated project folder in the `dsi-dssg` folder. The `dsi-dssg` folder should be visible in your home directory, if not, let the IT admin know and they will add it for you.

## Creating a notebook

In the launcher there are two options for notebook kernels, click either Python or R depending on which language you want to do your analysis with.

If you don't see those options, click the `+` icon on the tab area to create a new tab and the launcher should appear.

## Opening a Terminal window

Often you will want a Terminal window for more flexibility to issue commands (e.g `rm`, `cp`, `ls`, `git`, `pip`, `R`, etc.). The Terminal will require some basic knowledge of Linux shell commands.

To open a Terminal window, simply go to the launcher again and click the `Terminal` icon.

## Installing packages

### R

You can call `install.packages` in one of your notebook cells. Remove the `install.packages` call after the package is finished installing to avoid installing it repeatedly. 

Another option is to open a Terminal window and launch an R session there with the command `R`. Then run `install.packages` in the R session.

### Python

Open a Terminal window and enter the command `pip install --user <package>` replace `<package>` with whatever you want to install.

Remember to include the `--user` option in the command or else the package will not be there after you log out and log back in to JupyterHub.

## Logging out

To log out go to `File` on the top left and click `Log Out`. 

## Troubleshooting

Sometimes JupyterLab may run out of memory or freeze. First save all your work if you can. Then to restart your server (i.e. get a new Docker container) go to `File` on the top left and click `Hub Control Panel` then click `Stop My Server` and finally `Start My Server`.

You can see how much memory you're using on the bottom info bar beside `Mem:`. Each user is limited to 32GB of memory. More can be requested if needed.