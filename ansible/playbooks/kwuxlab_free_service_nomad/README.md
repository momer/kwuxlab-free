# Kwuxlab Free - Service Vault

This playbook installs and configures the [Nomad](https://www.nomadproject.io/)
service on the target nodes.

Hashicorp [Nomad](https://www.nomadproject.io/) is, "A simple and flexible 
scheduler and orchestrator to deploy and manage containers and 
non-containerized applications across on-prem and clouds at scale."

## Features

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

## Requirements

### External

1. Consul
    1. Must be installed/configured on the target hosts/inventory.
2. Vault
   1. Vault must be installed and bootstrapped on all primary datacenter
      server nodes.
   2. A Vault token with access to the `kv-v1` target namespace must be
      generated.

### Internal

#### Playbook Variables

1. `target_vault_addr`: The address of an unsealed Vault server. 
   - NOTE: Kwuxlab **Pro** automatically discovers this address via Consul DNS.
       - Kwuxlab Free expects that it is hard-wired here, and is susceptible to
         failure in the event of node failure/downtime.
2. `vault_master_token`: Vault token with access to the `kv-v1` store.
