## v1.1.2

### Fix
* Fix E405 Remote package tasks should have a retry.
* Use to_nice_json to manage packages list.
* Fix E203 Most files should not contain tabs.
* Fix E404 Doesn't need a relative path in role.

## v1.1.1

### Fix
* Set empty dependencies line to fix Galaxy warning.
* Deprecation warning in favor of debops.netbase and debops.resources role.

## v1.1.0

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

## v1.0.0

### Features
* Manage localhost line in /etc/hosts.
* Manage ipv4 line in /etc/hosts.
