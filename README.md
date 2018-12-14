GCP-Instances-Fixes
=========

Este es un role para arreglar problemas usuales con las instancias en GCP en diferentes situaciones como despues de reiniciar, conectarse mucho por SSH, etc. Son fixes a nivel sistema operativo y es recomendable aplicarlos por las dudas despues de reiniciar una instancia GCP. Este Role ademas programa tareas cron para que cada fix se vuelva a aplica al reiniciar las instancias.

El "Fix RO filesystem" deja un log en la env var "NAVENT_LOG_CRON_SCHEDULE_READONLY_FILESYSTEM_FIX" ademas de grabar un log en /tmp/.

Requirements
------------

- Ubuntu 16
- Ansible 2.7

Role Variables
--------------

Las variables soportadas son opcionales.

```
# Enable/Disable options
gcp_inst_fix_sshguard_timeout: yes
gcp_inst_fix_readonly_filesystem: yes
gcp_inst_fix_dns_resolution_fail: yes
gcp_inst_fix_sshguard_timeout_schedule: yes
gcp_inst_fix_readonly_filesystem_schedule: yes
gcp_inst_fix_dns_resolution_fail_schedule: yes

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
