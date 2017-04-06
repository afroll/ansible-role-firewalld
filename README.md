# Ansible Role: firewalld

Install and configures firewalld on RedHat/Centos 7

## Requirements

Tested on RedHat 7 & CentOS 7

## Example playbook

Basic playbook using the default variables. In will install and enabled firewalld and open SSH port.

```yml
- hosts: all
  roles:
    - ansible-role-firewalld
```

Playbook with custom variables.

```yml
- hosts: all
  roles:
    - ansible-role-firewalld
  vars:
    firewalld_state: latest
    firewall_debug: true
    firewalld_rules:
      ssh:
        port: 22
        protocol: tcp
        state: enabled
        zone: public
        permanent: true
      http:
        port: 80
        protocol: tcp
        state: enabled
        zone: public
        permanent: true
      https:
        port: 443
        protocol: tcp
        state: enabled
        zone: public
        permanent: true
```

## Role Variables

firewalld state( `present | latest | absent` )

```yml
firewalld_state: latest
````

Print firewall rules ( `true | false` )

```yml
firewall_debug: false
```

Add or remove firewall rules

```yml
firewalld_rules:
  ssh:
    port: 22
    protocol: tcp
    state: enabled
    zone: public
    permanent: true
```

## Dependencies

There are no dependencies for this role.

## License

MIT

## Author Information

Apostolos Tovletoglou [ansible-role-firewalld](https://github.com/tovletoglou/ansible-role-firewalld)
