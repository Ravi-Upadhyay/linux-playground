# Command Line

> Graphical user interfaces make easy tasks easier, while command line interfaces make difficult tasks possible

There is one cheatsheet on the [Linux Wiki](https://github.com/Ravi-Upadhyay/linux-playground/wiki/My-Cheat-sheet)

___

## Index

- Structure of Command
- Commands
    - Sudo
- Virtual Terminal (VT)
- Turning off Graphical Desktop

___

## Structure of Command

Every command has three parts- (1) Command (2) Options (3) Arguments

```bash
command [--options][arguments]

```

___

## Commands

### Sudo
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
