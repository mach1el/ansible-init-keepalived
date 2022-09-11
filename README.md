# Ansible initialize Keepalived

![Version](https://img.shields.io/github/v/release/mach1el/ansible_init_keepalived?color=brown&style=plastic) ![License](https://img.shields.io/github/license/mach1el/ansible_init_keepalived?color=purple&style=plastic)

Ansible role for initialize keepalived configuration,as default it won't enable keepalived on systemd,this role using to generate configuration for docker container [mich43/keepalived](https://github.com/mach1el/docker-keepalived)

## Role tree
```
.
├── defaults
│   └── main.yml
├── files
│   └── 99-non-local-bind.conf
├── handlers
│   └── main.yml
├── LICENSE
├── meta
│   └── main.yml
├── README.md
├── tasks
│   ├── add_configuration_file.yml
│   ├── binding_nonlocal_ip.yml
│   ├── install_packages.yml
│   └── main.yml
├── templates
│   ├──  keepalived.conf.j2
│   └──  node.sh.j2
└── vars
    └── main.yml
```

## Default variables
```
tcp: true
check_service: true
disable_keepalived: true

KA_MASTER: "10.10.92.170"
KA_BACKUP: "10.10.92.171"
KA_SV_PORT_CHECK: 80
KA_IFACE: "ens192"
KA_ROUTE_ID: "51"
KA_VIP: "10.10.92.250/24"
```

* `tcp`: If true it will check *TCP* port service else it will be *UDP*
* `check_service`: Tell keepalived to use script 
* `KA_*`: Variables for keepalived configuration

## Playbook
```
---
- name: Init keepalived on MASTER and BACKUP
  hosts: all
  roles:
   - 'mach1el.ansible_init_keepalived'
```