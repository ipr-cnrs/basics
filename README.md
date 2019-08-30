# Basics

This content is mainly deprecated and i start using [Debops Netbase role][debops netbase role]
which comes with most of this configuration (more and better).
The [Debops Ifupdown role][debops ifupdown role] can manage the DNS search and nameservers,
[see the documentation][debops ifupdown dns] for more informations and the
[Debops Resolvconf role][debops resolvconf role] can also give more possibilities.

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
    * [Hosts](#hosts)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

Manage some basics configuration for IPR's servers.

## Role Variables

* **basics__domain** : Domain to use [default : `{{ ansible_domain }}`].
* **basics__hosts_localhost_manage** : If the localhost (127.0.0.1) line should be managed [default : `false`].
* **basics__hosts_localhost_content** : Content of the localhost (127.0.0.1) line [default : `localhost.localdomain localhost`].
* **basics__hosts_ipv4_manage** : If the ipv4 address line should be managed [default : `false`].
* **basics__hosts_ipv4_content** : Content of the ipv4 address line [default : `{{ ansible_hostname }}.{{ basics__domain }} {{ ansible_hostname }}`].
* **basics__proxmox_*disable** : Allow to disable the management of some files by Proxmox for LXC containers [default : `[]`].
* **basics__resolvconf_packages** : List of Resolvconf packages to install [default : `resolvconf`].
* **basics__resolvconf_enabled** : Enable or disable support for Resolvconf [default : `False`].
* **basics__resolvconf_domains** : List of domains used as search suffixes with Resolvconf [default : `{{ ansible_domain }}`].
* **basics__resolvconf_nameservers** : List of nameservers to use to resolv host names with Resolvconf [default : `{{ ansible_dns.nameservers }}`].
* **basics__resolvconf_service_name** : The Resolvconf service name to manage [default : `resolvconf`].

## Example Playbook

* If you want to manage both localhost (127.0.0.1) and permanent IP (ipv4) lines :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.basics
      basics__hosts_localhost_manage: true
      basics__hosts_ipv4_manage: true
```

* If the domain is not defined on the remote host, you should set the `basics__domain` variable :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.basics
      basics__domain: 'mydomain.org'
      basics__hosts_ipv4_manage: true
```

## Configuration

### Hosts

Ensure to have the correct fqdn and hostname in /etc/hosts :
- You can define the domain if it's not correct on the remote host.
- You can choose to define the localhost (127.0.0.1) line content.
- You can choose to define the permanent ip (ipv4) line content.
  - All other lines that contains hostname without this permanent ip address will be removed.

For LXC containers, you also have the possibility to disable the management of some files (/etc/hosts,…) by Proxmox. See [Proxmox wiki about LXC][wiki proxmox lxc].

## Resolvconf

* If specified, Resolvconf is installed to fix the domain's informations given by the DHCP server.
* Configure a default configuration file with the given informations (list of domains and nameservers).
* Ensure to restart the service if any modification in configuration file.

## Development

This source code comes from our [Gogs instance][basics source] and the [Github repo][basics github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR here :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][basics source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][basics source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[gogs to github hook]: https://stackoverflow.com/a/21998477
[basics source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.basics
[basics github]: https://github.com/ipr-cnrs/basics
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/
[wiki proxmox lxc]: https://pve.proxmox.com/wiki/Linux_Container#_guest_operating_system_configuration
[debops netbase role]: https://docs.debops.org/en/master/ansible/roles/debops.netbase/index.html
[debops ifupdown role]: https://docs.debops.org/en/master/ansible/roles/debops.ifupdown/index.html
[debops resolvconf role]: https://docs.debops.org/en/master/ansible/roles/debops.resolvconf/index.html
