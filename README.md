# wg-action

WireGuard GitHub Action to access our internal registries from GitHub actions.

## Setup

This action requires you to define a set of input parameters.

```
name: access-cluster
on:
  push:
    branches:
      - "main"

jobs:
  test_access_cluster:
    runs-on: ubuntu-latest
    steps:
      - name: Install WG
        uses: promaton/wg-action@main
        with:
          interface_private_key: "${{ secrets.INTERFACE_PRIVATE_KEY }}"
          interface_address: "${{ secrets.INTERFACE_ADDRESS }}"

          peer_public_key: "${{ secrets.PEER_PUBLIC_KEY }}"
          peer_allowed_ips: "${{ secrets.PEER_ALLOWED_IPS }}"
          peer_endpoint: "${{ secrets.PEER_ENDPOINT }}"

          # Optional
          interface_dns: "${{ secrets.INTERFACE_DNS }}"
```
