# Check Docker Volumes

This small script seeks for unused volumes on you `/var/lib/docker/volumes`
directory.

## Why

On normal usage of `docker` you may use images that will setup volumes, to
store data. Database images are probably the most common ones.

However, whenever you remove a container that created a volume you must pass the
`-v` option to the `docker rm ` command. Because the default behavior is to keep
the volumes, that way if you still need the data it will be still there.

Even knowing about this you might end up with a lot of volumes just sitting
around on your disk.

### Usage

Just call the script, it will list the directories on `/var/lib/docker/volumes`
and check with the volumes associated with you containers with the
`docker inspect` command. It will list the name of the unused volumes and will
report how much space they are taking your disk.
