Добавление или блокировка пользователя
Используются переменные:
(обязательные)
user_name - уникальное для сервера имя пользователя
ssh_pub_key - публичный ssh ключ (или ключи), добавляется в authorized_keys
(опциональные)
groups_users - список групп в которые дополнительно нужно добавить пользователя (по умолчанию пользователь уже добавляется в группу $user_name)
user_shell - стандартная оболочка (по умолчанию: /bin/bash)
use_sudo - разрешение sudo (по умолчанию: false)
locked - блокировка учетной записи (по умолчанию: false)

Для каждого нового пользователя или каждой особой группы в playbook.yml нужно добавлять новый блок по примеру:  
```
...
  hosts: hostname,...
  become: true
  vars:
    user_name: username
    ssh_pub_key: |
      ssh-ed25519 ssh-ed25519 AAA...someusername@fmedia.tech
      ssh-ed25519 ssh-ed25519 BBB...someusername@fmedia.tech
    groups_users:
      - webadmin
      - ...
  tasks:
  - import_tasks: add-user.yml
```
