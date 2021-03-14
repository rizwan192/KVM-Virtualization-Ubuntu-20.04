
# KVM-Virtualization-Ubuntu-20.04

 This process demonstates Installing VMs on Ubuntu 20.04 using KVM
. All the commnads are run with sudo privilages. To run commnads as sudo we need to use the following command

```bash
suod su -
```

1. Checking if the host machine supports virualization.If it is more than "0" then our machine can support virtialization.

```bash
egrep -c '(vmx|svm)' /proc/cpuinfo
```
 Here we can see our machine supports kvm as the output is 12

![](images/1.png)

2. Then installing qemu-kvm and libvirt:

```bash
apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virtinst virt-manager
```
* ```qemu-kvm``` - software that provides hardware emulation for the KVM hypervisor.

* ```libvirt-daemon-system```- configuration files to run the libvirt daemon as a system service.

* ```libvirt-clients``` - software for managing virtualization platforms.

* ```bridge-utils``` - a set of command-line tools for configuring ethernet bridges.

* ```virtinst``` - a set of command-line tools for creating virtual machines.

* ```virt-manager``` - an easy-to-use GUI interface and supporting command-line utilities for managing virtual machines through libvirt

3. Once the packages are installed, the libvirt daemon will start automatically. You can verify it by typing:

```bash
ystemctl is-active libvirtd
```
here in the output we can see that it is activated

![](images/2.png)

4. To be able to create and manage virtual machines, you’ll need to add your user to the “libvirt” and “kvm” groups. To do that

```bash
usermod -aG libvirt $USER
usermod -aG kvm $USER
````

```$USER``` is an environment variable that holds the name of the currently logged-in user.

5. Lastly with we can check the network connectivity by the following command
```bash
brctl show
```
In the output we can see that we have a succesful NAT connection

![](images/3.png)

A bridge named “virbr0” is created during the installation process. This device uses NAT to connect the guests' machines to the outside world