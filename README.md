MariaDB Maxscale Ansible role
=============================

Install and configure MariaDB Maxscale for Debian Jessie.


Requirements
------------

I have many issues with systemd. You can use my [bootstrap role](https://github.com/HanXHX/ansible-debian-bootstrap) for removing systemd on your system.

Role Variables
--------------

### Global

- `maxscale_version`:
- `maxscale_threads`:
- `maxscale_log_messages`:
- `maxscale_log_trace`:
- `maxscale_log_debug`:
- `maxscale_logdir`:
- `maxscale_cachedir`:
- `maxscale_piddir`:

### Servers

- `maxscale_servers`:

Example:

```
maxscale_servers:
  - name: 'myserver1'
    address: '10.0.0.1'
    port: '3306'
    protocol: 'MySQLBackend'
    serv_weight: 1
    monitoruser: 'maxscale' # Overwrite global settings
    monitorpw: 'secure_password' # Overwrite global settings
```

### Routers

- `maxscale_rw_routers`:

Example:

```
maxscale_rw_routers:
  - name: 
    servers:
      - 'server1'
      - 'server2'
    user: 'maxscale'
    passwd: 'password'
```

### Listeners

- `maxscale_cli_listener`:
- `maxscale_cli_listener_address`:
- `maxscale_cli_listener_port`:
- `maxscale_debug_listener`:
- `maxscale_debug_listener_address`:
- `maxscale_debug_listener_port`:

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
