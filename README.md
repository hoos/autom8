Kojak - Autom8
=======================

Kojak Autom8 is fully integrated DevOps circuit that uses Openshift Origin and Fabric8 to deploy applications in the cloud.

![GitHub Logo](/slides/00.png)

Kojak started off as a collection of scripts which were used to automate the installation and configuration of the Koji build system. It was part of a productization effort to encourage the adoption of Koji for use in development, testing and staging environments.  The scripts included in this repository can be used to create a complete DevOps circuit with Source Control Manager, Continious Integration, Artifact Repository Manager and Testing Suite.
 
Tool Chain
----------

Kojak Autom8 installs Openshift Origin and Fabric which provide industry reconised opensource toolchain designed to allow developers to build, test, deploy, promote, release and replicate product builds in a consistent and predictable way.  The long term goal is to provide a DevOps platform to allow users to familiarize themselves with the DevOps aproach and tools.   

Installation Prerequisites
---------------------------

Kojak is a virtual appliance and it not recommended that you install directly on your workstation.  The Installation options will build a virtual machine for you which will be accessible from your local host.  If you already have a virtual machine you can install Kojak directly on that machine and skip the virtual machine provisioning stage.  Kojak has been successfully installed and tested on CentOS 7+ and RHEL 7+.

For more information about virtualization see below:

CentOS http://wiki.centos.org/HowTos#head-fb1ff7e71fb5f2f511cda8c68cb6ba5f6e8decae 

Fedora http://fedoraproject.org/wiki/Virtualization?rd=Tools/Virtualization

It is recommended that the system be updated before beginning the installation.  A fast internet connection is also required in order to facilitate the downloading of any package dependancies.

Minimum System Requirements
--------------------------- 

The virtual machine is configured with the following default specifications:

1. 8GB RAM
2. 64GB Disk Space

Your local host should be configured with the following minimum specifications:

1. Centos/RHEL 7+ or Fedora 18+ with virtualization package group
2. 16GB RAM
3. 128 GB Disk Space 

Installation Prerequisites
--------------------------

Create the virtual machine with the create-vm script.  You can modify the varibles in the script to control alloted resources but it is recommeded that you stick with the defaults. On your localhost execute the following commands.
```
[root@localhost]# git clone https://github.com/kojak/autom8.git
[root@localhost]# cd autom8
[root@localhost]# ./create-vm
```
Add the following to your /etc/hosts file on your localhost in order to resolv the microservices shipped with Kojak Autom8 as part of the DevOps Cicuit.
```
192.168.122.100 example.com master.example.com fabric8.example.com fabric8-master.example.com docker-registry.example.com gogs.example.com nexus.example.com jenkins.example.com
```
Installation Instructions
------------------------

Login into the virtual machine (see configuraiton notes for login credentials) and checkout the contents of the Kojak Autom8 git repository to a suitable directory on your vanilla virtual machine and execute the kojak executable.
```
[root@localhost]# yum -y install git
[root@localhost]# mkdir workspace
[root@localhost]# cd workspace 
[root@localhost]# git clone https://github.com/kojak/autom8.git
[root@localhost]# cd autom8
[root@localhost]# ./auto8
```
Or as a one liner.
```
yum -y install git && mkdir workspace && cd workspace && git clone https://github.com/kojak/autom8 && cd autom8 && ./autom8
```

At this stage the system is fully installed and configured.  

You can now browsing to the Fabric8 web console via http://fabric8.example.com with the following credentials:

1. username: admin
2. password: admin

To configure new users login into the vitual machine and execute the following:
```
htpasswd -b /etc/openshift/users.htpasswd <user> <password>
```

Configuration Notes
-------------------
The Kojak virtual machine is configured with a set of default options.  

1. OS: CentOS 7
2. Hostname: master.example.com
3. IP Adress: 192.168.122.100
4. Subnet Mask: 255.255.255.0

You can access the virtual machine via ssh at 192.168.122.100 using the following credentials:

1. username: root
2. password: root

Known Issues and How to Report Them
-----------------------------------

Execute the autom8-diag script and send the output via a github ticket.

See http://github.com/sbadakhc/autom8/issues?state=open

Discussion
----------

Join our community at https://plus.google.com/u/0/communities/103028582394768375364
