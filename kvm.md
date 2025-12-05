[Back to top](README.md)

# Virtualization

┌─────────┐
│  virsh  │
└─────────┘ 
┌────────────┐
│ libvirt(d) │
└────────────┘ 
┌─────────────────────┐ ┌───────────┐
│       qemu          │ │ Emulation │
└─────────────────────┘ └───────────┘ 
┌─────┐ ┌─────────────┐
│ kvm │ │ passthrough │
└─────┘ └─────────────┘ 
┌─────────────────────┐
│      hardware       │
└─────────────────────┘ 

## Check

```
cat /proc/cpuinfo

vmx flags	: vnmi preemption_timer posted_intr invvpid ept_x_only ept_ad ept_1gb flexpriority apicv tsc_offset vtpr mtf vapic ept vpid unrestricted_guest vapic_reg vid ple shadow_vmcs pml ept_violation_ve ept_mode_based_exec
```

If vmx (svm for AMD) flags are present on your Intel you are good to go.

## Install

```
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
```
Install all required packages for ubuntu 24.04.

```
sudo systemctl enable --now libvirtd
```
Enable libvirtd service

```
sudo usermod -aG libvirt,kvm $USER
```
Current user can now manage virtual machines.
