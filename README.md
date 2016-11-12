vagrant-provision
=========
Will provision local VMs on VirtualBox and generate an inventory file
with the dynamic infomration of the created hosts for you to be able to run your
playbook on the generated inventory.

Requirements
------------
VirtualBox version 5.1.8
Vagrant version 2.8.6
ansible version 2.1.2.0

Role Variables
--------------
- where you would like the generated vagrant folder to reside. 
  defaults to {{ playbook_dir }}
  vagrant_dir: "{{ playbook_dir }}/vagrant"
  

- where you would like the generated inventory file named local to reside
  default to {{ playbook_dir }}/inventories/
  inventory_output_dir: "{{ playbook_dir }}/inventories"
  
- A list of hosts to create (OS, Memory, IP and name) and a list of host groups for your inventory so your
  hosts can be part of. if you have a group 'webservers' you can add some hosts to this group.
  vagrant_hosts:
    - name: "default1"
      box: "bento/ubuntu-16.04"
      ip: "192.168.13.10"
      ram: 1024
      user: "vagrant"
      groups:
        - "default_group1"
        - "default_group2"
    - name: "default2"
      box: "bento/ubuntu-16.04"
      ip: "192.168.13.11"
      ram: 1024
      user: "vagrant"
      groups:
        - "default_group2"
  host_groups:
    - "default_group1"
    - "default_group2"

Dependencies
------------


Example Playbook
----------------
### SEE tests/test.yml
Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      vars:
        inventory_output_dir: "."
      remote_user: root
      roles:
        - vagrant-provision

License
-------
BSD

Author Information
------------------
Fullstack Developer @Tikal Knowledge DevOps group.