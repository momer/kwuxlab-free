# Kwuxlab Free - Service Consul

This playbook installs and configures the [Consul](https://www.consul.io/)
service (servers and clients) on the target nodes.

Hashicorp [Consul](https://www.consul.io/) will act as our foundational network
and service layer, monitoring node state, communication, and acting as a 
light distributed data store for some of our services (*e.g.* Vault).

## Features

- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Service (all ports) bound to private (tailscale)
  network; not accessible via internet.
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configure [Consul DNS](https://developer.hashicorp.com/consul/docs/discovery/dns)
  (Service discovery via DNS)
- [ ] ( :no_entry_sign: - Kwuxlab Pro Only) Configure and enable
  [Consul Access Control Lists (ACLs)](https://developer.hashicorp.com/consul/tutorials/security/access-control-setup-production)
- [x] :heavy_check_mark: Consul installation

Support Kwuxlab/InfraCasts to get these awesome features AND awesome tutorials
on how to make use of this code at https://infracasts.com

## Requirements

### Variables

1. `target_consul_raw_key`: Key which Consul will use for encryption across
   all nodes in the cluster.

