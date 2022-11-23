# Kwuxlab Free - Common Base (configuration)

This playbook installs and configures a number of base applications
for the target node(s).

## Features

- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Non-root sudoer user creation
  - Includes configuration to allow non-root user with Ansible
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Log-rotation & Journalctl max disk usage settings
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) NTP installation/configuration to avoid time-drift
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Base firewall configuration via the Uncomplicated Firewall ([UFW](https://wiki.ubuntu.com/UncomplicatedFirewall))
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Secure SSH configuration
  - Includes configuration of authorized_hosts file
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Fail2Ban configuration
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Hostname configuration
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Tailscale installation & bootstrapping
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Stateful storage with details of 
 ansible playbook execution (version, etc.) on remote
 host for future debugging/upgrade reference.
- [x] :heavy_check_mark: [Docker installation & base configuration](/ansible/playbooks/kwuxlab_free_common_base)
- [x] :heavy_check_mark: [Python/python3-pip installation/configuration](/ansible/playbooks/kwuxlab_free_common_base)
- [x] :heavy_check_mark: [Envoy proxy installation/base configuration](/ansible/playbooks/kwuxlab_free_common_base)

Support Kwuxlab/InfraCasts to get these awesome features AND awesome tutorials
on how to make use of this code at https://infracasts.com

## Requirements

### Variables

1. `default_local_timezone`: Default timezone to be configured on the node
2. `target_packages`: List of packages to install/update
