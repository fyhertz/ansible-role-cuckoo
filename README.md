Ansible role: Cuckoo Sandbox
============================

An Ansible role automating the deployment of [Cuckoo Sandbox](https://cuckoosandbox.org/), a malware analysis system.

Current limitations:

- Only libvirt/KVM is supported right now
- Probably only works on Ubuntu 16.04
- You still need to manually write most of your \<machinery\>.conf


Requirements
------------

At least Ansible 2.2 is required.


Role Variables
--------------

TODO!

Dependencies
------------

- [debops.libvirt](https://github.com/debops/ansible-libvirt) If libvirt is used for your VMs
- [geerlingguy.nginx](https://github.com/geerlingguy/ansible-role-nginx)
- [geerlingguy.mysql](https://github.com/geerlingguy/ansible-role-mysql) If you enable cuckoo distributed

```
$ ansible-galaxy install geerlingguy.nginx geerlingguy.mysql debops.libvirt
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: fyhertz.cuckoo,  cuckoo_enable_web_interface: True}
```

Running the test.yml playbook
-----------------------------

This playbook was written to test the role inside a [Vagrant](https://www.vagrantup.com/) box.

```
cd ansible-role-cuckoo/tests
vagrant up --provider libvirt
ansible-playbook -i inventory test.yml
```

License
-------

BSD

Author Information
------------------

- Simon Guigui
- Hugo Genesse
- Based on [this](https://github.com/breachintelligence/ansible-cuckoo)
