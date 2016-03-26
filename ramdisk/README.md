# Ram disk

This script will mount and unmount ramdisks obeying the configuration on a
file on your home directory named `.ramdisks`

## Why

Yes, I know that it is possible to setup ramdisks on the `fstab` but this
script covers a very specific case for me, probably you should use `fstab`
instead of this script.

### My case
I have an encrypted home directory on the computer and for that reason setting
up a ramdiks on `fstab` will fail if I specify a mount point inside my home
dir.

I like to use ramdisks whenever I have to work with projects that will
compile, build, minify, and whatever other process that will create a lot of
files that won't really help me while developing every time that I hit
`CTRL + S` to save my work.

Also I am using Docker to do most of my work, for that reason I cannot make
a sysmlink to a ramdisk that is mounted outside the directory shared with the
container.

### Usage

Create a file named `.ramdisks` on your home directory.

The file's format is very simple, every line defines a ramdisk.
First the desired size, then a comma and then the full path to the desired
mount point.

There is an example file, named `ramdisks.example`

If you call `ramdisk` or `ramdisk mount` the script will try to mount the
ramdisks specified by the file.

If you call `ramdisk umount` it will unmount the ramdisks.

### Important

The script will refuse to mount a ramdisk if:
 * The mount point does not exists
 * The mount point have non-hidden children
