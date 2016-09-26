MariaDB Maxscale Ansible role
=============================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-HanXHX.maxscale-blue.svg)](https://galaxy.ansible.com/HanXHX/maxscale/) [![Build Status](https://travis-ci.org/HanXHX/ansible-maxscale.svg?branch=master)](https://travis-ci.org/HanXHX/ansible-maxscale)

Install and configure MariaDB Maxscale for Debian Jessie.

Requirements
------------

None.

Role Variables
--------------

See: [default vars](defaults/main.yml).

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: maxscale
      roles:
         - { role: HanXHX.maxscale }

License
-------

GPLv2

Author Information
------------------

- Twitter: [@hanxhx_](https://twitter.com/hanxhx_)
