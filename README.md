# Exec Binding and Exec Action Compendium
A compendium for the [Exec Binding](https://www.openhab.org/addons/bindings/exec/) and [Exec Action](https://www.openhab.org/docs/configuration/actions.html#exec-actions) of openHAB. This integrates the possibility to execute arbitrary shell commands to openHAB.

## Foreword

The Exec Binding or Exec Action are actually the most powerful tools you can use in openHAB. You can start, reboot or shutdown remote computers. You can run applications on the local openHAB server or on remote computers. You can run applications in different programming languages. One can run applications in different executable formats. One can interact arbitrarily with the operating system or arbitrarily with command line tools. You can read or write files. Or you can open a file and change or add something to it. You can also interact with databases and other systems. Applications can also be stopped and restarted. System services can be started, stopped or restarted. System monitoring or network monitoring is possible. In short, you can actually communicate with all kinds of computers (mini computers, single board computers, multimedia systems, consoles, robots, etc.).

You just have to know how.

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

## The principle of whitelist and blacklist

### Editing the exec.whitelist

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

