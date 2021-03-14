# KVM-Virtualization-Ubuntu-20.04

# KVM-Virtualization-Ubuntu-20.04

#Installing VMs on Ubuntu 20.04 using KVM

All the commnads are run with sudo privilages. To run commnads as sudo we need to use the following command

```bash
suod su -
```

1. Checking if the host machine supports virualization.If it is more than "0" then our machine can support virtialization.

```bash
egrep -c '(vmx|svm)' /proc/cpuinfo
```
 Here we can see our machine supports kvm as the output is 12

![](images/1.png)

2. 

