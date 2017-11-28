Role Name
=========

This role help an administrators to operate VSP Gx00 arrays

Requirements
------------

No requirements

Role Variables
--------------

View vars/main.yml

Dependencies
------------

No dependencies

Example Playbook
----------------

```yaml

#This play is executed when update_mode var is "true" and ensure that role is up to date. By default update var is "false"
- hosts: ansible
  user: root
  tasks:
    - name: Ensure that role are up to date
      command: ansible-galaxy install --force {{ item }}
      with_items:
        - miquelMariano.VSP_Gx00
      when:
        - update_mode | default(False)
      tags: update
      ignore_errors: yes

#Role folder must be exist. If not, the playbook not found role and fails. You shoud make dir manually "mkdir /etc/ansible/my_role"

- hosts: ansible
  user: root
  roles:
   - VSP_Gx00

```

Usage
-------

```
ansible-playbook playbooks/VSP_Gx00_ops.yml -e "add_host=true" --tags lock,nickname,unlock
```

License
-------

BSD

Author Information
------------------

[miquelMariano.github.io](https://miquelmariano.github.io)  | [@miquelMariano](https://twitter.com/miquelMariano)
