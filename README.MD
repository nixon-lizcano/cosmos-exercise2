## Requirements
- Vagrant >= 2.2.19
- Ansible core >= 2.13.1
- Virtualbox >= 6.1.34 r150636 (Qt5.6.2)
- Python >= 3.8.10

## Ansible structure
- site.yml -> Main playbook
- db.yml -> Postgres server's playbook
- web.yml -> Node API & APP's playbook