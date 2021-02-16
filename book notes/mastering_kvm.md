---
cards-deck: tech::kvm
---

# OS virtualization/partitioning
#card
* container based virtualization
* process isolation and resource management provided by kernel
* each container has own FS/processes/memory/devices
+ no need to emulate syscall
- cannot emulate different OS

# protection ring
#card
* ring 0 is kernel mode, most privileged, interacts directly with HW
* ring 1&2 unused
* ring 3 is user mode
* Without HW support, vmm runs at ring 0, guest OS at ring 1.

# full virtualization
#card
* privileged instructions are trapped, dynamically rewritten and emulated using binary translation.
+ unmodified guest OS
- large overhead

# paravirtualization
* guest OS modified in order to allow running at ring 0
* guest kernel aware of virtualized
* syscall become hypercall (guest kernel talk to VMM directly)
+ better performance than full virtualization

# HW-assisted virtualization
* efficiently use full virtual with hardware capabilities. e.g. Intel VT, AMD-V
* VMM runs at ring -1
* guest kernel runs at ring 0
* guest has direct access to resources without emulation or os modification
+ better performance

# VMM
* responsible for monitoring and controlling VM
* provide virtual hardware
* vm lifecycle management
* vm migration
* resource allocation

# type 1 hypervisor
* VMM runs directly on top of hardware, aka bare metal, embedded, native hypervisor
+ less overhead
- doesn't favor customization

# type 2 hypervisor
* vmm runs on top of host OS, aka hosted hypervisor
+ wide range of hardware support

# xen
* operate on both para virtual and hardware assisted or full virtual (HVM)
* guest OS called domains.
* Dom Us are unprivileged guest systems
* Dom 0 is privileged domain, special guest, control Dom Us.

# KVM
* turns linux kernel into hypervisor
* use QEMU for hardware emulation in userland.
* Separate qemu-kvm process for each VM by libvirtd.
* vm properties defined in /etc/libvirt/qemu
