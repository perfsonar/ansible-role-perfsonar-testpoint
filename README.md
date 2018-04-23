Role Name
=========

This roles installs and configure a perfSONAR testpoint.

Requirements
------------

This role is meant to work with any perfSONAR supported distro:

  - CentOS: http://docs.perfsonar.net/install_centos.html
  - Debian/Ubuntu: http://docs.perfsonar.net/install_debian.html

The hosts must be manageable through Ansible including access to some Ansible modules.  We recommend that you bootstrap Ansible on your hosts prior to running this role.  A good way to do that is using https://galaxy.ansible.com/robertdebock/bootstrap/ as a very first role.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Role Tags
---------

Some tags are used in the role, they are meant to run only or skip part of the process.  The following tags are existing:

  - ps::install
  - ps::configure

If, for example, you only want to install the perfSONAR software without configure it automatically, you can run: `ansible-playbook site.yml --skip-tags "ps::install"`

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache 2.0

Author Information
------------------

This role is provided by the perfSONAR team.  See http://www.perfsonar.net and https://github.com/perfsonar/ for more information.

