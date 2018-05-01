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

  - `defaults/main.yml` contains the following variables:
    - `ntp_servers` is a list of NTP servers to configure on the perfSONAR testpoint
    - `perfsonar_optional_packages` is the list of additional optional packages you want to install with the testpoint bundle, see http://docs.perfsonar.net/install_debian.html#optional-packages or http://docs.perfsonar.net/install_centos.html#optional-packages for more information.

  - `vars/Debian.yml` and `vars/RedHat.yml` contains distro specific settings, but shouldn't need to be altered for a regular install.

Role Tags
---------

Some tags are used in the role, they are meant to run only or skip part of the process.  The following tags are existing:

  - ps::install : only install perfSONAR packages and their dependencies
  - ps::preconfig : make sure your system is ready for perfSONAR configuration
  - ps::config : only configure any already installed perfSONAR package

Examples,

  - If you only want to install the perfSONAR software without configuring it automatically, you can run:
    `ansible-playbook site.yml --tags "ps::install"`
  - If you have already installed the perfSONAR packages and you only want to change an already existing config, you can run:
    `ansible-playbook site.yml --skip-tags "ps::install"`

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

