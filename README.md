# Exec Binding and Exec Action Compendium
A compendium for the [Exec Binding](https://www.openhab.org/addons/bindings/exec/) and [Exec Action](https://www.openhab.org/docs/configuration/actions.html#exec-actions) of openHAB. This integrates the possibility to execute arbitrary shell commands to openHAB.

## Foreword

The Exec Binding or Exec Action are actually the most powerful tools you can use in openHAB. You can start, reboot or shutdown remote computers. You can run applications on the local openHAB server or on remote computers. You can run applications in different programming languages. One can run applications in different executable formats. One can interact arbitrarily with the operating system or arbitrarily with command line tools. You can read or write files. Or you can open a file and change or add something to it. You can also interact with databases and other systems. Applications can also be stopped and restarted. System services can be started, stopped or restarted. System monitoring or network monitoring is possible. In short, you can actually communicate with all kinds of computers (mini computers, single board computers, multimedia systems, consoles, robots, etc.).

You just have to know how.

## Assumption

I assume that openHAB is installed on a Linux operating system.

## Requirements

Of course, you have to be well acquainted with your operating system and its applications.

A Linux operating system is usually more versatile than a Windows operating system. With a few settings, Windows can also be optimized a bit, which ultimately allows us to do a lot more with Windows. This will be explained below. You can use many tools. So well under Windows as under Linux. A few Linux-typical tools can also be installed under Windows. This is also something we want to do. So we bring together some of the possible examples for both operating systems. You don't have to find an alternative tool and explain its operation additionally. Nevertheless, Linux probably offers more operating possibilities from the operating system than Windows. But at the end of the day, why not be able to operate both systems through openHAB?

In addition to the knowledge of the operating systems, one must of course know that both operating systems run applications differently, that there are different file formats, etc. And finally, you also need some knowledge about the tools and applications you want to use.

## Optimizing a Windows operating System

I assume that you use Minium Windows 10.

### Installing openSSH-Server

### Enable Wake on LAN

### Installing PsTools

### Adding Linux tools to Windows

## Our little helper which

The `which` command shows in which directory the specified command is found. `which` searches for an executable file only in directories specified in the `PATH` environment variable and returns only the first file (to show all files with the same name, use the -a option).

Why it makes sense? Because sometimes the same application exists multiple times. Accordingly, it makes sense that you angbit the exact path.

```
which python
/usr/bin/python
```

or

```
which python3
/usr/bin/python3
```

would not make any difference. You can also run `python` or `python3`. But Python is a very good example that there are virtual Python environments ([virtualenv](https://virtualenv.pypa.io/en/latest/)). To make it simple: I can install packages in a `virtualv` independently from the ones the complete system uses for Python. If I would use `/usr/bin/python3` instead of `/path/to/virtual_environment/bin/python3`, the system does not know these installed packages. So the dependencies cannot be resolved! Thus, the program cannot be executed without errors.

To stay with the Python example, you can change to the virtual environment directory, activate that virtual environment, and use `which` to check which Python is started.

```
cd /path/to/virtual_environment/
source bin/activate
which python3
/path/to/virtual_environment/bin/python3
```

So at least you can use `/path/to/virtual_environment/bin/python3 <file>.py` to run your Python code without any errors!

Python, of course, is not the only good example of why it makes sense to ultimately specify the full path to the executed application:

* Environment variables can be set up locally for one user or globally for all users.
* An application was simply not added to the `PATH` variable. With which you will not find it then, but you can use which to check if this application has been added to the `PATH` variable. Accordingly, you can still add this variable to the `PATH` variable or you can directly use the full path to the application for openHAB.
* Using the example of system services, you can see that this application also executes with the full path specification. This is due, for example, to the fact that the environment variables may not be loaded.
* Using `SSH` as an example, one also experiences time and again that applications cannot be executed because they are often only specified in the local `PATH` variable.
* On Linux, the `executables` are often moved to standard directories such as `/usr/bin/`, `/sbin/`, `/usr/local/bin/` or referenced with `symbolic links` when they are installed. In Windows there is usually a directory for installed programs for `x86` and for `64-bit`, but the `exe` files are usually located there in subfolders from the manufacturer and the name of the program. Thus the PATH variable with Windows usually does not know the `Exe` file.
* A program was installed manually and is therefore not located in a directory used by the `PATH` variable.

To reduce possible sources of error, we use `which` to figure out how to run an application as independently of the environment variables as possible.

## Environment variables

### PATH

#### Linux

#### Windows

### PYTHONPATH

## The principle of whitelist and blacklist

A `whitelist` or `blacklist` is a positive or negative list that can be used to protect systems in the IT environment. A `blacklist` prohibits the execution of something, while the `whitelist` allows it.

In openHAB the `exec.whitelist` is used for the `Exec Binding` and for the `Exec Action`. Therefore you have to explicitly allow openHAB to execute this command.

### Editing the exec.whitelist

If your openHAB configuration folder is in `/etc/openhab` you can find the `exec.whitelist` in `/etc/openhab/misc`. You can change it with `sudo nano /etc/openhab/misc/exec.whitelist`. If this folder or file does not exist you have to create it:

```
sudo -u openhab mkdir /etc/openhab/misc
sudo -u openhab touch /etc/openhab/misc/exec.whitelist
```

Before you add a `<command>`, you can still test this command:

```
sudo -u openhab <command>
```

With `sudo -u openhab` you make sure that the `openhab` user, which should have been created during the installation of openHAB, can execute this command. If it's not the case, openHAB can not run this command.

At least there is one important point. Each command needs a new line in the `exec.whitelist`. This means as example:

```
<command>
<command2>
<command3>
```

Of course you can add comments with `#`:

```
<command> # needed to shutdown the pc
<command2> # playing Minecraft
<command3> # another useless comment
```

What do I mean with `<command>`? Well with `<command>` I mean the whole line you will enter in your command line interface before pressing enter. So your `<command>` can be very long like as example: `/usr/bin/sshpass -p <password> /usr/bin/ssh <user>@<ip> "echo Hello World!"`.

Another important point is that every time I use `<` and `>` you have to replace it with your parameter. This could be as example the ip address, username or password from your remote computer by replacing `<ip>`, `<user>` and `<password>`. So every time I use `<` and `>` I will use it as placeholder.

## What is a command line and how to run commands on a command line?

### Run commands locally

### Run commands remotely

### Shell? Bash? Terminal? Command Line? - An introduction 

### Batch and Bash commands equivalents

## What about scripts?

### Bash scripts

### Shell scripts

### Batch scripts

## Wake on LAN, Reboot and Shutdown

## Runnning System Services

### Split down a system service

## Running different programming languages

### Running Python

### Running Java

### Running C

### Running C++

### Running C#

### Running JavaScript

### Running PHP

## Running applications

### Running executables

### Running Steam

### Running Unity

### Running Chrome

### Running Firefox

### Running VLC

## Running ROS (Robot Operating System)

## Runing system tools

## Running network tools

## File interactions

### Moving files and folders

### Creating files and folders

### Renaming files and folders

### Deleting files and folders

### Change permissions of files and folders

### Change owners

### Reading a file

### Writing a file

### Append content to a file

## Interacting with databases

## Creating and Restoring Backups

### Archive files

### Image files

### Git

## Interacting with openHAB via Command Line

### Using Curl

### Using the Karaf Console

#### Karaf Commands

#### Rules

#### Things

#### Items

