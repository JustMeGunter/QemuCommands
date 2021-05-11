# QEMU

- Converting VMDK to QCOW2
-- `qemu-img convert -f vmdk -O qcow2 disk.vmdk disk.qcow2
-- **qemu-img** is the built-in qemu image manipulation tool.
-- **convert** tells qemu.
-- **-f vmdk** *(optional)* this tells qemu what type of file you will convert to.
-- **-O qcow2** this tells qemu what type of file you will convert to.
-- **disk.vmdk** is the file you are converting from **disk.qcow2** output file.

- Running QCOW2 image.
-- `qemu-system-x86_64 -m 4G -smp 4 --enable-kvm disk.qcow2`
-- **qemu-system-x86_64** this commands launches qemu in x64bit mode.
-- **-m 4G** allocates 4 GB of ram to the virtual machine.
-- **-smp 4** suggest qemu to use the number refrenced of cores of your CPU to the virtual machine.
-- **-enable-kvm** enables KVM on your vm to help with perfomance.
-- **disk.qcow2** is the path to the image you want to run.

- Mount qcow2
-- `qemu-nbd --connect=/dev/nbd0 image.qcow2
-- **qemu-nbd** is the built-in qemu loads the nbd kernel module.
-- **--connect=/dev/nbd0** specifies disk image used as network block device.
-- **image.qcow2** image to be mounted.
-- `fdisk /dev/nbd0 -l` list nbd-mapped partitions.
-- `mount /dev/nbd0 /mnt` mount point to make it accesible. 
-- `umount /mnt` when finished using.
-- `qemu-nbd --disconnect /dev/nbd0` disconnect.
