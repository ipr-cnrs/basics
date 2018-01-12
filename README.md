# Basics

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
* **basics__hosts_ipv4_manage** : If the ipv4 (lan) line should be managed [default : `false`].
* **basics__hosts_ipv4_content** : Content of the ipv4 (lan) line [default : `{{ ansible_hostname }}.{{ basics__domain }} {{ ansible_hostname }}`].

## Example Playbook

* If you want to manage both localhost (127.0.0.1) and permanent IP (lan/ipv4) lines :

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
      basics__hosts_localhost_manage: true
      basics__domain: 'mydomain.org'
````

## Configuration

### Hosts
- Ensure to have the correct fqdn and hostname in /etc/hosts.
  - You can define the domain if it's not correct on the remote host.
  - You can choose to define the localhost (127.0.0.1) line or/and the ipv4 (lan) line.

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
