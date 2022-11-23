# Kwuxlab Free - Service Vault

This playbook installs and configures the [Vault](https://www.vaultproject.io/)
service on the target nodes.

Hashicorp [Vault](https://www.vaultproject.io/),
"secures, stores, and tightly controls access to tokens, passwords,
certificates, API keys, and other secrets in modern computing."

## Features

- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Service (all ports) bound to private (tailscale)
  network; not accessible via internet.
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Integrate with Consul via ACL token
- [x] :heavy_check_mark: Basic Vault installation

Support Kwuxlab/InfraCasts to get these awesome features AND awesome tutorials
on how to make use of this code at https://infracasts.com

## Requirements

### External

1. Consul
   1. Must be installed/configured on the target hosts/inventory.

#### Host variables

This playbook expects a `datacenter` variable to be set on all hosts targeted,
such that Vault is aware of the topology.
