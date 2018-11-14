GCP-Instances-Fixes
=========

Este es un role para arreglar problemas usuales con las instancias en GCP en diferentes situaciones como despues de reiniciar, conectarse mucho por SSH, etc. Son fixes a nivel sistema operativo y es recomendable aplicarlos por las dudas despues de reiniciar una instancia GCP.

Requirements
------------

- Ubuntu 16
- Ansible 2.7

Role Variables
--------------

Las variables soportadas son opcionales.

```
# Read Only filesystem fix
gcp_inst_fix_rofs_src: "/dev/sda1"
gcp_inst_fix_rofs_path: "/"
gcp_inst_fix_rofs_fstype: "ext4"

# SSH Guard connection time out fix
gcp_inst_fix_ssh_sshguard_enabled: "no"

# DNS resolution fail fix
gcp_inst_fix_ssh_sd_resolved_enabled: "yes"
```

Example Playbook
----------------

```
    - hosts: servers
      roles: 
         - gcp-instances-fixes
```

Author Information
------------------

Augusto Mendoza (amendoza@navent.com)
