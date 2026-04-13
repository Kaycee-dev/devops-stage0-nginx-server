# Lane Model

## Lane Types

- `control`: delivery-state upkeep and packet issuance
- `provisioning`: provider, instance, user bootstrap, access-path setup
- `hardening`: SSH config, sudoers, firewall policy
- `nginx`: Nginx install, `/`, `/api`, service enablement
- `ssl`: DNS, Certbot, HTTPS, redirect behavior
- `proof`: logs, journal, evidence capture

## Lane State Machine

1. `drafted`
2. `queued`
3. `ready`
4. `running`
5. `verifying`
6. `blocked`
7. `review_ready`
8. `merged`
9. `failed`
10. `archived`

## Failure Taxonomy

- `access_risk`
- `env_missing`
- `dns`
- `tls`
- `config`
- `service_state`
- `docs_proof`

## Green Contract

- `targeted_green`: narrow fix or sub-check passed
- `lane_green`: the lane's declared checks passed
- `gate_green`: the relevant gate is review-ready
- `release_green`: the live HTTPS domain, proof, and submission pack are complete
