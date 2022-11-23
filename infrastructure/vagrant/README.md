# Kwuxlab / Infrastructure / Vagrant

> NOTE: Unless you're working with a beast of a computer, and can beef up the
resources on your Vagrant machines, I highly recommend paying a few bucks for
a hosting provider (AWS/Hetzner) to use the development environment instead.
>
> On some machines, the Vagrant execution of Ansible playbooks
is pretty quick, while on others, I've experienced excruciatingly slow
execution.

## Pre-requisites & Configuration

You don't need to be an expert to get started with Vagrant, but I do recommend
being familiar with how it works. Going through the official
[Getting Started](https://learn.hashicorp.com/tutorials/vagrant/getting-started-install?in=vagrant/getting-started)
would be a good use of your time, if you're going this route!

1. [Install Vagrant](https://www.vagrantup.com/downloads)
   - You may need to install/configure `virtualbox` as well,
      as the provider.

2. *Optional*: Change the network configuration for the virtual machines 
   to-be-created.
   - The included [Vagrantfile](./Vagrantfile) has already been pre-configured
     to assign each node in the cluster a specific IP address on a private 
     network to make configuration of the [ansible scripts](../../ansible)
     easy.
   - If you want to update the pre-configured network addresses, simply change
     the `node.vm.network :private_network, ip: "192.168.56.5"` settings in
     [Vagrantfile](./Vagrantfile), and make sure to update the IP addresses
     within the [ansible inventories file](../../ansible/inventories).

## Deploy

Once `vagrant` is installed, start the virtual machines:

```sh
$ cd infrastructure/vagrant
$ vagrant up
```

This will take some time to download the machine image and bootstrap the 
actual VMs.

Once the command completes, you can check the status of the machines via

```sh
infrastructure/vagrant$ vagrant status
Current machine states:

node1                     running (virtualbox)
node2                     running (virtualbox)
node3                     running (virtualbox)
node4                     running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

## Next steps

You can now follow-along with the [ansible scripts](../../ansible/README.md)
with your virtual machines!

### Destroying the Virtual Machines

Once you're done working with these VMs, they can be destroyed by running

```sh
$ vagrant destroy
```