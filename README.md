# RCLONOID

Rclonoid is a small and simple command line tool for backing up ZFS file systems to any [rclone](https://rclone.org/) remote. It is inspired by the great tool [syncoid](https://github.com/jimsalterjrs/sanoid), hence the name.

### Idea

The above mentioned syncoid is a replication tool that uses `zfs send/receive` to back up any ZFS file system. Thus, it requires ZFS on the receiving side.

My use case is _simpler_: Back up any ZFS file system to a NAS device whose directories are locally mounted via NFS. I decided to do the actual backup via `rclone`, which makes it more general, because you then can back up your ZFS file systems to any _remote_.

### Usage

At the moment, I do not know how far this really will go. But at least, there are two use cases: back up a single ZFS file system, and back up all _eligible_ ZFS file systems. Eligible means that a file system must be mounted. Otherwise, it will not be backed up.

There are at least these two typical commands:

```
rclonoid single pool/data backup
rclonoid all backup
```

Here `pool/data` represents a single mounted ZFS file system, and `backup` must be a fully configured and reachable rclone remote.
