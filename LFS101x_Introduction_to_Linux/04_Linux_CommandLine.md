# Command Line

> Graphical user interfaces make easy tasks easier, while command line interfaces make difficult tasks possible

There is one cheatsheet on the [Linux Wiki](https://github.com/Ravi-Upadhyay/linux-playground/wiki/My-Cheat-sheet)

___

## Index

- Structure of Command
- Sudo
- Virtual Terminal (VT)
- Turning off Graphical Desktop
- System Maintenance - Shutdown Command
- Locating Applications
- Links
  - Hard Link
  - Soft Link
- Navigating the directory history
- Pipes
- Installing Software

___

## Structure of Command

Every command has three parts- (1) Command (2) Options (3) Arguments

```bash
command [--options][arguments]

```

___

## Sudo
Sudo allows users to run programs using the security privileges of another user, generally root(superuser). In some systems we might need to set up and enable sudo.

___

## Virtual Terminal (VT)

Virtual Terminals (VT) are console sessions that use the entire display and keyboard outside of a graphical environment. Such terminals are considered "virtual" because, although there can be multiple active terminals, only one terminal remains visible at a time.

One virtual terminal (usually number one or seven) is reserved for the graphical environment. To switch between VTs, press CTRL-ALT-function key for the VT.

___

## Turning off the Graphical Desktop

Display manager runs as a service. GDM - GENOME Display Manager

To stop the service: 
`sudo systemctl stop gdm` or 
`sudo telinit 3` or 
`sudo service gdm stop`

To start the service: 
`sudo systemctl start gdm` or 
`sudo telinit 5` or 
`sudo service gdm start`

___

## System Maintenance - Shutdown Command

- The preferred method to shut down or reboot the system is to use the shutdown command.
- The halt and poweroff commands issue `shutdown -h` to halt the system; reboot issues `shutdown -r`.
- Both the commands should be run as super user.

___

## Locating Applications

- In general, executable programs and scripts should live in the /bin, /usr/bin, /sbin, /usr/sbin directories, or somewhere under /opt
- They can also appear in /usr/local/bin and /usr/local/sbin, or in a directory in a user's account space, such as /home/student/bin.
- `which` and `whereis` are two utilities to locate programs

___

## Links

The `ln` utility is used to create hard links and (with the `-s` option) soft links, also known as symbolic links or symlinks. These two kinds of links are very useful in UNIX-based operating systems.

### Hard Link

Suppose that file1 already exists. A hard link, called file2, is created with the command:

```bash
$ ln file1 file2
```

Note that two files now appear to exist. However, a closer inspection of the file listing shows that this is not quite true.

```bash
$ ls -li file1 file2
```

The `-i` option to `ls` prints out in the first column the **inode number**, which is a unique quantity for each file object. This field is the same for both of these files; what is really going on here is that it is only one, file but it has more than one name associated with it, as is indicated by the 2 that appears in the ls output. Thus, there was already another object linked to file1 before the command was executed.

Hard links are very useful and they save space, but you have to be careful with their use, sometimes in subtle ways. For one thing, if you remove either file1 or file2 in the example, the **inode object** (and the remaining file name) will remain, which might be undesirable, as it may lead to subtle errors later if you recreate a file of that name.

If you edit one of the files, exactly what happens depends on your editor; most editors, including vi and gedit, will retain the link by default, but it is possible that modifying one of the names may break the link and result in the creation of two objects.

### Soft Link

Soft (or Symbolic) links are created with the -s option, as in:

```bash
$ ln -s file1 file3
$ ls -li file1 file3
```

Notice file3 no longer appears to be a regular file, and it clearly points to file1 and has a different inode number.

Symbolic links take no extra space on the filesystem (unless their names are very long). They are extremely convenient, as they can easily be modified to point to different places. An easy way to create a shortcut from your home directory to long pathnames is to create a symbolic link.

Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media,  which may or may not be currently available or even exist. In the case where the link does not point to a currently available or existing object, you obtain a dangling link.
___

## Navigating the directory history:

The `cd` command remembers where you were last, and lets you get back there with `cd -`. For remembering more than just the last directory visited, use `pushd` to change the directory instead of `cd`; this pushes your starting directory onto a list. Using `popd` will then send you back to those directories, walking in reverse order (the most recent directory will be the first one retrieved with popd). The list of directories is displayed with the `dirs` command.

___

## Pipes:

```bash
command1 | command2 | command3
```

- Allows Linux to combine the actions of several commands into one. 
- This is extraordinarily efficient because command2 and command3 do not have to wait for the previous pipeline commands to complete before they can begin hacking at the data in their input streams.
- Furthermore, there is no need to save output in (temporary) files between the stages in the pipeline, which saves disk space and reduces reading and writing from disk.

___

## Installing Software

- The core parts of a Linux distribution and most of its add-on software are installed via the **Package Management System**. 
- There are two broad families of package managers: those based on Debian and those which use RPM as their low-level package manager. 

___
