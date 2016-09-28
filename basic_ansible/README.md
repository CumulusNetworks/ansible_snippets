# Ansible Examples for Virtual Infrastructure


## Overview

This repo contains some examples of how to deploy configurations and automation to virtual infrastructure. This demonstration is part of the ["Agile Network Deployment" webinar](http://go.cumulusnetworks.com/wbr-agile-deployment)


## Virtualizing a Network with Cumulus VX

[Cumulus VX](https://cumulusnetworks.com/cumulus-vx/) is a virtual machine
produced by Cumulus Networks to simulate the user experience of configuring a
switch using the Cumulus Linux network operating system.
[Vagrant](https://www.vagrantup.com/) is an open source tool for quickly
deploying large topologies of virtual machines. Vagrant and Cumulus VX can be
used together to build virtual simulations of production networks to validate
configurations, develop automation code, and simulate failure scenarios.

Vagrant topologies are described in a Vagrantfile, which is a Ruby program that
tells Vagrant which devices to create and how to configure their networks.
`vagrant up` will execute the Vagrantfile and create the reference topology
using Virtualbox. It will also use Ansible to configure the out-of-band
management network.

## Prerequisites

Before running this demo or any of the other demos based on the [Reference Topology](https://github.com/CumulusNetworks/cldemo-vagrant), install
[VirtualBox](https://www.virtualbox.org/manual/ch02.html) and
[Vagrant](https://www.vagrantup.com/downloads.html) using the
installation instructions from their website. The version of Vagrant and Virtualbox
available in your distribution's package manager may be out of date, so
installing via the preferred sources is recommended. This example was last
tested with **Vagrant 1.8.4**.

**NOTE: Do not use Vagrant version 1.8.5, there are known issues that should be rectified in v1.8.6**

On an Ubuntu 16.04 machine, this can be done with the following commands:

    # Download the Vagrant Software
    $ wget https://releases.hashicorp.com/vagrant/1.8.4/vagrant_1.8.4_x86_64.deb

    # Install the Vagrant Software
    $ sudo dpkg -i vagrant_1.8.4_x86_64.deb

    # Install Git
    $ sudo apt-get install git

    # Install Cumulus plugin for Vagrant
    $ vagrant plugin install vagrant-cumulus

## Getting Started

Install the prerequisites mentioned above.

### Download the Virtual Topology

**Windows:** Download the topology by visiting [https://github.com/CumulusNetworks/cldemo-vagrant/archive/master.zip](https://github.com/CumulusNetworks/cldemo-vagrant/archive/master.zip) in a web browser. Unzip the file to a location of your choosing.

**Linux:** Make sure you already have Git installed and clone the repository

    $ git clone https://github.com/cumulusnetworks/cldemo-vagrant or running the following command on a Linux

### Deploy the Virtual Topology

    # Move to the Directory where you've downloaded the topology.
    $ cd cldemo-vagrant
    
    # Turn on the Management Server and Management Switch
    $ vagrant up oob-mgmt-server oob-mgmt-switch
    
    # Turn on nodes in the dataplane
    $ vagrant up spine01 spine02 leaf01 leaf02 server01 server02


### Login to the Management Server

    $ vagrant ssh oob-mgmt-server

### Fetch your Configurations and Automation

    vagrant@oob-mgmt-server$ git clone https://github.com/CumulusNetworks/ansible_snippets.git

### Deploy to Virtual Infrastructure
You can deploy individual features by choosing the appropriate YAML file, OR you can deploy all of the features by using the *all.yaml* playbook as shown below:

    vagrant@oob-mgmt-server$ cd ./ansible_snippets/basic_ansible/
    vagrant@oob-mgmt-server$ ansible-playbook ./all.yaml



![Cumulus icon](http://cumulusnetworks.com/static/cumulus/img/logo_2014.png)

### Cumulus Linux

Cumulus Linux is a networking focused Linux distribution that runs on top of industry standard networking hardware. It enables the latest Linux applications and automation tools on networking gear while delivering new levels of innovation and ﬂexibility to the data center.

For further details please see: [cumulusnetworks.com](http://www.cumulusnetworks.com)
