Ansible role: Libvirt
=====================

Install libvirt and other relevant packages to enable virtualization
on the host, for creating virtual machines and virtual networks.
Optionally, install virtmanager for a GUI to interact with libvirt.

Role Variables
--------------

```
ENTRY POINT: main - Install libvirt

        Install libvirt and other relevant packages to enable
        virtualization on the host, for creating virtual machines and
        virtual networks. Optionally, install virtmanager for a GUI to
        interact with libvirt.

OPTIONS (= is mandatory):

- libvirt_install_virtmanager
        If true, install virtmanager
        [Default: False]
        type: bool

- libvirt_packages
        List of packages to install
        [Default: ['qemu-kvm', 'libvirt-daemon-system', 'libvirt-
        clients', 'bridge-utils']]
        elements: str
        type: list

- libvirt_virtmanager_packages
        List of packages for virtmanager
        [Default: ['virt-manager']]
        elements: str
        type: list

```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/libvirt,main,wandansible.libvirt
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.libvirt
      src: https://github.com/wandansible/libvirt

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: libvirt_hosts
      roles:
         - role: wandansible.libvirt
           become: true
           vars:
             libvirt_install_virtmanager: true
