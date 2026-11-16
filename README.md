# Gitea PanelTutor fixture

Minimal, real-world deployment used to exercise PanelTutor Apps with a random
public application instead of a bespoke one.

- Upstream project: [go-gitea/gitea](https://github.com/go-gitea/gitea)
- Official rootless image: `docker.gitea.com/gitea:28.4.0-rootless`
- Runtime user: `1000:1000` (image default)
- Persistence: named volumes for `/var/lib/gitea` and `/etc/gitea`
- Networking: only `expose: 3000`; PanelTutor owns ingress and probes
- Health: `GET /api/healthz`

The compose file intentionally declares no host ports, no host bind mounts and
no root user. Those are PanelTutor hardening requirements, not Gitea changes.
