## v1.X

### Enhancements
* Allow to install Resolvconf.
* Manage Resolvconf base configuration file.
* Restart Resolvconf service if any modification on configuration file.
* Resolvconf default configuration is set from ansible facts.

## v1.0.3

### Fixes
* Ensure to disable management of files by Proxmox only one time.

## v1.0.2

### Enhancements
* Disable the management of /etc/hosts by Proxmox.

## v1.0.1

### Enhancements
* Add example playbook.
* localhost line sould not contain hostname information (see https://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_hostname_resolution).
* Purge /etc/hosts of multiple lines that contains $HOSTNAME without the default ipv4 ip address.
* Purge conditions of /etc/hosts are the same as permanent ip address (ipv4).

## v1.0

### Features
* Manage localhost line in /etc/hosts.
* Manage ipv4 line in /etc/hosts.
