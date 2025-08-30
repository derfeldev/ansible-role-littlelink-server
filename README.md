# SPDX-FileCopyrightText: 2025 Pavel Dimov <@sagat79>
#
# SPDX-License-Identifier: AGPL-3.0-or-later

# Ansible Role: LittleLink Server

[![License: AGPL-3.0-or-later](https://img.shields.io/badge/License-AGPL%203.0--or--later-blue.svg)](https://spdx.org/licenses/AGPL-3.0-or-later.html)
[![REUSE status](https://api.reuse.software/badge/github.com/derfeldev/ansible-role-littlelink-server)](https://api.reuse.software/info/github.com/derfeldev/ansible-role-littlelink-server)

An Ansible role to install and configure [LittleLink Server](https://github.com/timothystewart6/littlelink-server), a lightweight DIY alternative to services like Linktree.

## Description

LittleLink Server is a lightweight DIY alternative to services like [Linktree](https://linktr.ee) and [many.link](https://many.link/). It's built using [Skeleton](http://getskeleton.com/), a dead simple, responsive boilerplate with branded styles for popular services.

**Note**: This Ansible role is based on the [LittleLink Server](https://github.com/timothystewart6/littlelink-server) project by [Timothy Stewart (Techno Tim)](https://github.com/timothystewart6), which is licensed under the MIT License.

This Ansible role provides:

- Docker container deployment
- Systemd service management
- Traefik reverse proxy integration
- Comprehensive configuration options
- Security hardening with HTTP headers

## Requirements

- Ansible 2.1+
- Docker
- Systemd
- Linux distribution (Debian, Ubuntu, ArchLinux, EL)

## Role Variables

### Main Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `littlelink_server_enabled` | `true` | Enable/disable the role |
| `littlelink_server_hostname` | `''` | Hostname for the service |
| `littlelink_server_path_prefix` | `/` | URL path prefix |

### Container Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `littlelink_server_version` | `latest` | Container image version |
| `littlelink_server_container_http_port` | `3000` | Container HTTP port |
| `littlelink_server_container_http_host_bind_port` | `''` | Host port binding |

### Traefik Integration

| Variable | Default | Description |
|----------|---------|-------------|
| `littlelink_server_container_labels_traefik_enabled` | `true` | Enable Traefik labels |
| `littlelink_server_container_labels_traefik_entrypoints` | `web-secure` | Traefik entrypoints |
| `littlelink_server_container_labels_traefik_tls` | `true` | Enable TLS |

### LittleLink Server Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `littlelink_server_meta_title` | `LittleLink Server` | Page title |
| `littlelink_server_meta_description` | `A lightweight DIY alternative to services like Linktree` | Page description |
| `littlelink_server_name` | `LittleLink Server` | Display name |
| `littlelink_server_bio` | `A lightweight DIY alternative to services like Linktree` | Bio text |
| `littlelink_server_theme` | `Dark` | Theme (Dark/Light) |

### Social Media Links

The role supports all major social media platforms including:

- GitHub, Twitter, Instagram, LinkedIn
- YouTube, Twitch, Discord, TikTok
- Facebook, Patreon, and many more

Set the corresponding variables (e.g., `littlelink_server_github`, `littlelink_server_twitter`) to enable them.

## Dependencies

- `community.docker` collection
- `devture.systemd_docker_base` role (optional, for systemd integration)

## Example Playbook

```yaml
---
- hosts: servers
  roles:
    - role: ansible-role-littlelink-server
      vars:
        littlelink_server_enabled: true
        littlelink_server_hostname: "links.example.com"
        littlelink_server_meta_title: "My Links"
        littlelink_server_name: "John Doe"
        littlelink_server_bio: "Software Engineer | Open Source Contributor"
        littlelink_server_github: "https://github.com/johndoe"
        littlelink_server_twitter: "https://twitter.com/johndoe"
        littlelink_server_linked_in: "https://linkedin.com/in/johndoe"
        littlelink_server_theme: "Dark"
```

## Integration with Mash Playbook

This role is designed to integrate with the [Mash Playbook](https://github.com/mother-of-all-self-hosting/mash-playbook). Add it to your `requirements.yml`:

```yaml
---
- src: git+https://github.com/derfeldev/ansible-role-littlelink-server.git
  version: main
  name: littlelink_server
  activation_prefix: littlelink_server_
```

## License

This project is licensed under the AGPL-3.0-or-later License - see the [LICENSE](LICENSE) file for details.

## Author Information

- **Pavel Dimov** - [@sagat79](https://github.com/sagat79)
- **Company** - DIMOV

## Original Project

- **LittleLink Server** - [@timothystewart6](https://github.com/timothystewart6)
- **Original Repository** - [https://github.com/timothystewart6/littlelink-server](https://github.com/timothystewart6/littlelink-server)
- **License** - MIT License

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For support, please open an issue on the GitHub repository.
