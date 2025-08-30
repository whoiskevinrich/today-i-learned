# File Management

## Moving Files

### mv

files can be moved with `mv`

```
mv [source] [destination]

# example
mv file.txt /home/user/documents/
```

### rsync

`rsync` is a powerful tool for synchronizing files and directories between two locations. It can be used for local file transfers as well as remote transfers over SSH.

```
rsync [options] [source] [destination]

# example
rsync -ah /home/user/documents/ user@remote:/home/user/backup/
```

common options for `rsync` include:

- `-a`: Archive mode (preserves permissions, timestamps, symbolic links, etc.)
- `-v`: Verbose output (shows the progress of the transfer)
- `-z`: Compress file data during transfer
- `-h`: Human-readable output (e.g., shows file sizes in KB, MB, etc.)