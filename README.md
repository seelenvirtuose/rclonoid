# RCLONOID

Rclonoid is a small and simple command line tool for replicating ZFS file systems to any [rclone](https://rclone.org/) remote. It is inspired by the great tool [syncoid](https://github.com/jimsalterjrs/sanoid), hence the name.

### Idea

Syncoid is a replication tool that uses `zfs send/receive` to replicate any ZFS file system. Thus, it requires ZFS on the receiving side.

My use case is somewhat simpler: Replicate any ZFS file system to a NAS device whose directories are locally mounted via NFS. I decided to do the actual replication with `rclone`, which makes it more general. Thus, you can replicate your ZFS file systems to any configured rclone remote, even cloud storage. But you do not need ZFS on the receiving side.

### Usage

There are two use cases:

- Replicate a single ZFS file system.
- Replicate all eligible ZFS file systems. Eligibility is determined by the mounted flag of a ZFS file system. If it is not mounted, then it is not eligible and thus not replicated.

Examples:

```
rclonoid single pool/data backup
rclonoid all backup
```

Here `pool/data` represents a single mounted ZFS file system, and `backup` must be a fully configured and reachable rclone remote.
