# RCLONOID

Rclonoid is a small and simple command line tool for replicating ZFS file systems to any [rclone](https://rclone.org/) remote. It is inspired by the great tool [syncoid](https://github.com/jimsalterjrs/sanoid), hence the name.

### Idea

Syncoid is a replication tool that uses `zfs send/receive` to replicate any ZFS file system. Thus, it primarily requires ZFS on the receiving side.

Rclonoid, on the other hand, originated from the need to replicate ZFS file systems to a NAS device that does not have ZFS installed but serves its data via NFS.

The idea was born to do the actual replication with `rclone sync`, which makes it much more general. Thus, you can replicate your ZFS file systems to any configured rclone remote, even cloud storage if you wish.

### Usage

There are two use cases:

- Replicate a single eligible ZFS file system.
- Replicate all eligible ZFS file systems.
 
Eligibility is determined by the mounted flag of a ZFS file system. If it is not mounted, then it is not eligible and thus not replicated.

If running as a scheduled job, consider redirecting the output to a log file, because rclonoid prints out various log messages on the console.

Run the command without any arguments to get more information.
