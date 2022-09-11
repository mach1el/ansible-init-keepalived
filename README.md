# Ansible initialize Keepalived

Ansible role for initialize keepalived configuration,as default it won't enable keepalived on systemd,this role using to generate configuration for docker container [mich43/keepalived](https://github.com/mach1el/docker-keepalived)

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