# Mounting Raspberry Pi Images          

The official image files are at [here] [1]. To mount these on a 
filesystem you can use these tricks.

(first, extract the .img from the downloaded .zip)

## Gather required information

The image is a disk image (i.e. it contains a partition table and partitions).
We need to know the partition offsets within the image so that we can mount the filesystems.

    $ parted archlinuxarm-01-03-2012.img
    WARNING: You are not superuser.  Watch out for permissions.
    GNU Parted 3.1 
    Using .../archlinuxarm-01-03-2012.img
    Welcome to GNU Parted! Type 'help' to view a list of commands.
    (parted) unit    
    Unit?  [compact]? B    
    (parted) print    
    Model:  (file)
    Disk .../archlinuxarm-01-03-2012.img: 1977614336B
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    Disk Flags: 
    
    Number  Start       End          Size         Type     File system  Flags
     1      512B        100000255B   99999744B    primary  fat16        lba 
     2      100000256B  1977614335B  1877614080B  primary  ext3
    
    (parted) q    

## Mount the first partition

    sudo mount -o loop,offset=512 archlinuxarm-01-03-2012.img /mnt

## Mount the second partition

    sudo mount -o loop,offset=100000256 archlinuxarm-01-03-2012.img /mnt

## Acknowledgement

This is derived from a note written by [Andre Miller] [2] that has some further
information and discussion.

  [1]: http://www.raspberrypi.org/downloads

  [2]: http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux

