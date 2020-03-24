[![Travis (.org) branch](https://img.shields.io/travis/nl2go/ansible-role-ip-route/master)](https://travis-ci.org/nl2go/ansible-role-ip-route)
[![Ansible Galaxy](https://img.shields.io/badge/role-nl2go.ip_route-blue.svg)](https://galaxy.ansible.com/nl2go/ip_route/)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/nl2go/ansible-role-ip-route)](https://galaxy.ansible.com/nl2go/ip_route)
[![Ansible Galaxy Downloads](https://img.shields.io/ansible/role/d/47292.svg?color=blue)](https://galaxy.ansible.com/nl2go/ip_route/)

# Ansible Role: IP Route

An Ansible Role that manages IP routes.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    ip_route_configs: {}
        
IP routes are defined using `ip_route_configs` variable.
    
    ip_route_configs:
      eth0:
        - gateway: 172.0.1.1
          network: 172.0.1.0/24

The configuration above manages the route for the network `172.0.1.0/24` using the
gateway `172.0.1.1` over the device `eth0`.

The configuration is persisted within `/etc/network/{if-up.d|if-down.d}`.  

    ip_route_configs:
      eth0:
        - network: 172.0.1.0/24
          state: absent

Use `state: absent` to remove a specific route. Routes are identified by the `network`.

## Tags

Tags can be used to limit the role execution to a particular task module. Following tags are available:

- `ip_route`: Covers the full role lifecycle.
- `ip_route_config`, `config`: Applies required configuration.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
         - nl2go.ip_route
              
## Development
Use [docker-molecule](https://github.com/nl2go/docker-molecule) following the instructions to run [Molecule](https://molecule.readthedocs.io/en/stable/)
or install [Molecule](https://molecule.readthedocs.io/en/stable/) locally (not recommended, version conflicts might appear).

Use following to run tests:

    molecule test --all

## Maintainers

- [build-failure](https://github.com/build-failure)
- [pablo2go](https://github.com/pablo2go)

## License

See the [LICENSE.md](LICENSE.md) file for details.

## Author Information

This role was created by in 2020 by [Newsletter2Go GmbH](https://www.newsletter2go.com/).
