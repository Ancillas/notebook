# VM Tips and Tricks

## ToDo: Move this into a sub-folder

## Mount a qcow2 disk locally

Credit to maloo and Gilles
https://unix.stackexchange.com/questions/268460/how-to-mount-qcow2-image

First install guestmount (comes as part of libguestfs-tools in Centos6)

### CentOS6

```
yum install libguestfs-tools libguestfs
```

### Ubuntu 18.04

```
sudo apt-get install libguestfs-tools
```

### Mount the image

```
sudo mkdir /mnt/qcow-image
guestmount -a path_to_image.qcow2 -i --ro /mnt/qcow-image
```

You can manually specify mount points (within the image) using the -m option.
