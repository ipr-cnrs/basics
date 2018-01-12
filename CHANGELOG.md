## v1.0.X

## Enhancements
* Add example playbook.
* localhost line sould not contain hostname information (see https://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_hostname_resolution).
* Purge /etc/hosts of multiple lines that contains $HOSTNAME without the default ipv4 ip address.

## v1.0

### Features
* Manage localhost line in /etc/hosts.
* Manage ipv4 line in /etc/hosts.
