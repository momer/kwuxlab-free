# Kwuxlab Free

The Free Kwuxlab is a repository containing everything you need to get 
up-and-running with a "light" Hashicorp Cluster, and begin playing around with
Hashicorp 
[Consul](https://www.consul.io/), [Vault](https://www.vaultproject.io/), and
[Nomad](https://www.nomadproject.io/).

Note: this free lab is considered a playground environment, which will get you
up-and-running with a Hashicorp cluster quickly, but is missing a number of
bells-and-whistles that you may want in a more stable environment.

## Kwuxlab Free vs. Kwuxlab Pro

Kwuxlab **Free** is designed to be a playground environment, where you can get 
familiar with basic features of [Consul](https://www.consul.io/), 
[Vault](https://www.vaultproject.io/), and [Nomad](https://www.nomadproject.io/). 

Kwuxlab **Free** allows you to quickly deploy a fully functional Hashicorp cluster
on your local machine via VMs, so you can follow along with tutorials and
get familiar with the fantastic developer experience that the stack enables!

Kwuxlab **Pro** provides you with a complete set of tools to
deploy and comfortably maintain a
complete environment, including, at a high-level:

- Connecting all nodes in the environment via
Tailscale VPN, and using the dual-network configuration to deploy
sensitive applications (*e.g.* Consul) on the private network, 
while allowing internet-facing traffic via the Envoy proxy, managed by Nomad.
- Configuring and initializing Consul and Nomad Access Control Lists (ACLs)
   for secure authentication/authorization across services and Vault-managed
   secrets.
- And much, much, more (see below)!

Moving from the Kwuxlab Pro environment to a homelab/production environment
requires only that you add additional security where desired
(*e.g.* configuring cloud-provider firewalls).

### Features

1. [Infrastructure Environment](/infrastructure/README.md)
   - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Terraform modules and Terragrunt configuration for
     deployment on
     - [x] :heavy_check_mark: Hetzner Cloud
     - [ ] AWS
     - [ ] GCP
     - [ ] Azure
   - [x] :heavy_check_mark: Virtual machine deployment via [Vagrant](https://www.vagrantup.com/)

2. [Basic compute environment configuration](/ansible/playbooks/kwuxlab_free_common_base/README.md),
including basic security/quality-of-life settings:
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
   - [x] :heavy_check_mark: [Docker installation & base configuration](/ansible/playbooks/kwuxlab_free_common_base/README.md)
   - [x] :heavy_check_mark: [Python/python3-pip installation/configuration](/ansible/playbooks/kwuxlab_free_common_base/README.md)
   - [x] :heavy_check_mark: [Envoy proxy installation/base configuration](/ansible/playbooks/kwuxlab_free_common_base/README.md)

3. [Consul deployment/configuration](/ansible/playbooks/kwuxlab_free_service_consul/README.md)
   - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Service (all ports) bound to private (tailscale)
     network; not accessible via internet.
   - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configure [Consul DNS](https://developer.hashicorp.com/consul/docs/discovery/dns)
     (Service discovery via DNS)
   - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configure and enable
     [Consul Access Control Lists (ACLs)](https://developer.hashicorp.com/consul/tutorials/security/access-control-setup-production)
   - [x] :heavy_check_mark: [Consul Server/Client deployment and bootstrap](/ansible/playbooks/kwuxlab_free_service_consul/README.md)

4. [Vault deployment/configuration](/ansible/playbooks/kwuxlab_free_service_vault/README.md)
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Service (all ports) bound to private (tailscale)
      network; not accessible via internet.
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Integrate with Consul via ACL token
    - [x] :heavy_check_mark: Basic Vault installation

5. [Nomad deployment/configuration](/ansible/playbooks/kwuxlab_free_service_nomad/README.md)
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Service (all ports) bound to private (tailscale)
      network; not accessible via internet.
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configure and manage [Host Volumes](https://developer.hashicorp.com/nomad/tutorials/stateful-workloads/stateful-workloads-host-volumes)
      for stateful workloads
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Dynamic integration with upstream services (Vault, Consul)
      via Consul DNS/Service Discovery
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Authorization with Consul via Consul ACLs
      [Consul Access Control Lists (ACLs)](https://developer.hashicorp.com/consul/tutorials/security/access-control-setup-production)
    - [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configuration & Bootstrapping of Nomad 
      [Access Control Lists (ACLs)](https://developer.hashicorp.com/nomad/tutorials/access-control/access-control)
    - [x] :heavy_check_mark: Nomad installation
    - [x] :heavy_check_mark: Consul integration
    - [x] :heavy_check_mark: Vault integration

Support Kwuxlab/InfraCasts to get these awesome features AND awesome tutorials
on how to make use of this code at https://infracasts.com


## Getting Started

This repository makes use of git submodules, which you'll need to fetch. Don't worry,
it's pretty straight-forward; the commands below should fetch all required components!

1. Clone this repository
2. Begin by creating your target [infrastructure environment](/infrastructure/README.md)
   [/infrastructure/README.md](/infrastructure/README.md) for details.
3. Configure your machines with Ansible, securing them and
installing services like Tailscale, the Hashicorp stack, etc. See this project's
[/ansible/README](/ansible/README.md) for details.
