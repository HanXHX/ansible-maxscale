MariaDB Maxscale Ansible role
=============================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-HanXHX.maxscale-blue.svg)](https://galaxy.ansible.com/HanXHX/maxscale/) [![Build Status](https://travis-ci.org/HanXHX/ansible-maxscale.svg?branch=master)](https://travis-ci.org/HanXHX/ansible-maxscale)

Install and configure MariaDB Maxscale for Debian Jessie/Stretch.

Requirements
------------

Maxscale supports systemd... but initsysv support seems buggy.

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

Donation
--------

If this code helped you, or if you’ve used them for your projects, feel free to buy me some :beers:

- Bitcoin: `1BQwhBeszzWbUTyK4aUyq3SRg7rBSHcEQn`
- Ethereum: `63abe6b2648fd892816d87a31e3d9d4365a737b5`
- Litecoin: `LeNDw34zQLX84VvhCGADNvHMEgb5QyFXyD`
- Monero: `45wbf7VdQAZS5EWUrPhen7Wo4hy7Pa7c7ZBdaWQSRowtd3CZ5vpVw5nTPphTuqVQrnYZC72FXDYyfP31uJmfSQ6qRXFy3bQ`

No crypto-currency? :star: the project is also a way of saying thank you! :sunglasses:

Author Information
------------------

- Twitter: [@hanxhx_](https://twitter.com/hanxhx_)
