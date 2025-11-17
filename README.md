Ansible Role: Gluetun-docker
============================

Install Gluetun Docker Compose project.

- https://github.com/qdm12/gluetun
- https://hub.docker.com/r/qmcgaw/gluetun

Requirements
------------

Requires the following to be installed:
- docker
- docker compose

Role Variables
--------------

Common system variables:

```yaml
timezone: UTC
```

Common Docker projects variables:

```yaml
# Base directory for Docker projects
docker_projects_path: # /var/apps
```

Available role variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Docker project variables

gluetun_project_name: gluetun

# Gluetun project variables

gluetun_version: latest

# Gluetun port mappings
gluetun_ports:
  # - "8888:8888/tcp # HTTP proxy"
  # - "8388:8388/tcp # Shadowsocks"
  # - "8388:8388/udp # Shadowsocks"
  # - "9091:9091/tcp # Transmission Web UI"
  # - "51413:51413/tcp # BitTorrent protocol"
  # - "51413:51413/udp # BitTorrent protocol"

# Gluetun environment variables
gluetun_environment:
  # See https://github.com/qdm12/gluetun-wiki/tree/main/setup#setup
  VPN_SERVICE_PROVIDER: example
  VPN_TYPE: # openvpn | wireguard

  # OpenVPN:
  # OPENVPN_USER:
  # OPENVPN_PASSWORD:
  # ...

  # Wireguard:
  # WIREGUARD_PRIVATE_KEY:
  # WIREGUARD_ADDRESSES:
  # ...

  # Server list updater
  # See https://github.com/qdm12/gluetun-wiki/blob/main/setup/servers.md#update-the-vpn-servers-list
  # UPDATER_PERIOD: 24h
```

Dependencies
------------

This role depends on :
- [djuuu.docker_project](https://github.com/Djuuu/ansible-role-docker-project)

Example Playbook
----------------

```yaml
- hosts: example
  gather_facts: false

  roles:
    - djuuu.gluetun_docker
```

License
-------

Beerware License
