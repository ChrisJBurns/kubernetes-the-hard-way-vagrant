# kubernetes-the-hard-way-vagrant
Just a Vagrant file that sets up the machines ready for the Kubernetes The Hard Way Tutorial

As the tutorial has been modified so people can run it on non-Cloud infrastructure, it can sometimes be awkward to setup VM's separately. I have made this easier by just providing a single Vagrant file that you run that will provision the VM's necessary for the tutorial.

> NOTE: Due to the complexities and awkwardness `arm64` architectures on Macbooks and given VirtualBox doesn't support it with the Debian OS that the tutorial uses, I am instead using the `amd64` Debian image instead. This doesn't have an impact on the tutorial apart from needing to modify the initial `downloads.txt` file so that it downloads `amd64` binairies and files instead of `arm64` ones. Once that is done there is no impact (that I experienced) when running through the tutorial other than needing to replace the `arm64` references to `amd64` in the later parts of the tutorial.
>
> Example
> From: https://storage.googleapis.com/kubernetes-release/release/v1.28.3/bin/linux/arm64/kubectl
> To: https://storage.googleapis.com/kubernetes-release/release/v1.28.3/bin/linux/amd64/kubectl

## Prerequisites

- Have [Vagrant](https://www.vagrantup.com/) installed
- Have [VirtualBox](https://www.virtualbox.org/) installed

## Setup

To create the `jumpbox`, `server`, `node-0` and `node-1` VM's just run:

```shell
$ vagrant init
$ vagrant up
```

When `vagrant up` has been run, retrieve the ssh config by running:

```shell
vagrant ssh-config > ssh-config
```

Now you can go into each of the VM's using ssh like so:

```shell
ssh -F ssh-config jumpbox
```

Just to avoid any problems around root password, it is best to just set the root password to a simple to remember password for when you do some early steps around copying files from jumpbox to the other VM's. This is only needed until the SSH keys step, from then on, passwords are not needed.

Run the following to change the password of the root user in the VM's

```shell
$ ssh -F ssh-config server
$ sudo su 
$ sudo passwd
$ # Enter a password
```
