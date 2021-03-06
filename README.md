Role Name
=========

This role help an administrators to operate VSP Gx00 arrays

Requirements
------------

No requirements

Role Variables
--------------

All variables defined on vars/main.yml

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

00-lockresource | Update role and lock/unlock resources
```
ansible-playbook playbooks/VSP_Gx00_ops.yml -e "update_mode=true" --tags update,lock,unlock
```

01-add_host_to_hostgroup
```
pending...
```

02-delete_host_from_hostgroup
```
ansible-playbook playbooks/VSP_Gx00_ops.yml -e "delete_host=true" --tags lock,delete_host,unlock
```

03-delete_lun_path
```
ansible-playbook playbooks/VSP_Gx00_ops.yml -e "delete_lun_path=true ldev_id=09:00 inst=1" --tags lock,delete_lun_path,unlock
```

04-delete_ldev
```
ansible-playbook playbooks/VSP_Gx00_ops.yml -e "delete_ldev=true ldev_id=09:00 inst=1" --tags lock,delete_ldev,unlock
```

License
-------

BSD

Author Information
------------------

[miquelMariano.github.io](https://miquelmariano.github.io)  | [@miquelMariano](https://twitter.com/miquelMariano)
