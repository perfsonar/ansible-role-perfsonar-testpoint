perfSONAR-testpoint Ansible role
================================

This roles installs and configure a perfSONAR testpoint.

Requirements
------------

This role is meant to work with any perfSONAR supported distro:

  - CentOS: http://docs.perfsonar.net/install_centos.html
  - Debian/Ubuntu: http://docs.perfsonar.net/install_debian.html

The hosts must be manageable through Ansible including access to some Ansible modules.  We recommend that you bootstrap Ansible on your hosts prior to running this role.  This can be done manually or through roles provided by [DebOps][debops] or some bootstrap roles available on Ansible Galaxy like [robertdebock.bootstrap][rdbs] as a very first role.

It requires Ansible v2.5 at least.

Role Variables
--------------

The following variables can/should be defined for your host setup:

  - `perfsonar_os_update` defaults to True.  This causes the base OS to be updated.
  - `perfsonar_ntp_servers` is a list of NTP servers to configure on the perfSONAR testpoint, or an empty list, per default, if you want to use the perfSONAR provided NTP servers.
  - `perfsonar_disable_root_ssh` disable or keep ssh root access, the default is to disable it.
  - `perfsonar_psconfig_remote_remotes` list the URL of remote templates that should be added or deleted from each testpoint host.
     - provides the option to include options to the `psconfig remote add` command.

  - Some other variables are defined at the end of `default/main.yml` and in `vars/Debian.yml` and `vars/RedHat.yml` (those contains distro specific settings), but shouldn't need to be altered for a regular install.

Role Tags
---------

Some tags are used in the role, they are meant to run only or skip part of the process.  The following tags are existing:

  - `ps::install` : only install perfSONAR packages and their dependencies
  - `ps::config` : only configure any already installed perfSONAR package
  - `ps::running` : checks that your perfSONAR node is running as intended
  - `ps::monitor` : print some system info of your perfSONAR node

Examples,

  - If you only want to install the perfSONAR software without configuring it automatically, you can run:

        ansible-playbook site.yml --tags "ps::install"

  - If you have already installed the perfSONAR packages and you only want to change an already existing config, you can run:

        ansible-playbook site.yml --skip-tags "ps::install"

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: perfsonar-testpoint

License
-------

Apache 2.0

Author Information
------------------

This role is provided by the perfSONAR team.  See http://www.perfsonar.net and https://github.com/perfsonar/ for more information.


[debops]: https://debops.org/
[rdbs]: https://galaxy.ansible.com/robertdebock/bootstrap/
[debian-optional]: http://docs.perfsonar.net/install_debian.html#optional-packages
[centos-optional]: http://docs.perfsonar.net/install_centos.html#optional-packages
