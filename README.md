# UniFi Network MCP

Helm chart for deploying [sirkirby/unifi-network-mcp](https://github.com/sirkirby/unifi-network-mcp) on Kubernetes.

Exposes an MCP server over SSE that AI agents (e.g. Hermes) can use to manage UniFi network infrastructure.

## Install

```bash
helm install unifi-network-mcp oci://ghcr.io/geoberle/unifi-network-mcp-chart \
  -n unifi-network-mcp --create-namespace \
  -f values.local.yaml
```

## Configuration

Create a `values.local.yaml` with your UniFi controller credentials:

```yaml
unifi:
  host: "192.168.1.1"
  username: "admin"
  password: "your-password"
```

All available values:

| Key | Default | Description |
|---|---|---|
| `image.repository` | `ghcr.io/sirkirby/unifi-network-mcp` | Container image |
| `image.tag` | `latest` | Image tag |
| `service.port` | `3000` | MCP server port |
| `transport` | `sse` | MCP transport (`sse`, `stdio`, `http`, `streamable-http`) |
| `unifi.host` | `""` | UniFi controller hostname or IP |
| `unifi.port` | `443` | Controller port |
| `unifi.username` | `""` | Admin username |
| `unifi.password` | `""` | Admin password |
| `unifi.site` | `default` | UniFi site name |
| `unifi.verifySsl` | `false` | Verify controller TLS certificate |
| `resources.requests.cpu` | `100m` | CPU request |
| `resources.requests.memory` | `128Mi` | Memory request |
| `resources.limits.memory` | `256Mi` | Memory limit |
