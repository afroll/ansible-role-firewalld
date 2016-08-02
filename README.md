# Ansible Role: firewalld

Install and configures firewalld on RedHat/Centos 7

## Requirements

Tested on RedHat & CentOS 7

## Role Variables

Available variables are listed below, along with default values `defaults/main.yml`

    # Print firewall rules (true | false)
    firewall_debug: false

    # Add or remove firewall rules
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

## Dependencies

There are no dependencies for this role.

## Parent playbook

This role is a part of the playbook: [Aegir on CentOS 7](https://github.com/tovletoglou/ansible-playbook-aegir-centos).

## Example Playbook

Call the role with the default variables

    - hosts: webservers
      roles:
        - firewalld

Call the role and override the default variables

    - hosts: webservers
      roles:
        - firewalld
      vars:
        firewalld_rules:
          httpd:
            port: 80
            protocol: tcp
            state: enabled
            zone: public
            permanent: true
          mysqld:
            port: 3306
            protocol: tcp
            state: enabled
            zone: public
            permanent: true

## License

MIT
