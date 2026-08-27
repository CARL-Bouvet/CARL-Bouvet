# Carl Bouvet

Full-stack JavaScript engineer. Node/Bun back ends, Nuxt front ends, and the Docker Swarm and k3s clusters they actually run on. Seven years of JavaScript, working solo — which means I own the whole chain, from the query to the 3am incident.

Most of my public work lives here as **[agent-skills](https://github.com/CARL-Bouvet/agent-skills)**:
production knowledge distilled from real postmortems, packaged for AI coding agents. Every rule in it cost me hours or days to learn.

### What I actually do

**WebSocket ingestion that survives production.** I ingest live trades from about ten crypto exchanges. Connecting was never the hard part — the hard part is the socket that stays open while silently delivering nothing. Application-level ping/pong on top of the transport, zombie
detection, clean reconnect with no orphaned timers.

**Data at scale, and the ways it breaks.** MongoDB in depth: index-first with `.explain()`, grouped writes, the TTL that silently no-ops because the field isn't a `Date`, the engine cache that fights the container's memory cap. I've paid for each of those in production.

**Infrastructure I run myself.** Docker Swarm, then a single-node k3s cluster in real production — ingress reachable only through a WireGuard tunnel, CronJob backups, a dead-man's switch, reboot-durability tested live. I host what I ship and keep it alive.

**Vue and Nuxt, plus Three.js when the interface needs 3D** — including the Blender side:
glTF import, cleanup and re-export, Draco compression, and why your scene is slow. I shipped a browser game for a paying client.

### Not my ground

AWS, GCP, Firebase, Supabase. Managed cloud isn't where I work, and I'd rather tell you that now than learn it on your budget.

### Things I learned the expensive way

- A MongoDB TTL index on `Date.now()` does nothing. No error, no log. 127 GB, three weeks. 2 month of work lost. This isn't my first scar, but it's a nice one.
- `kubectl top` under-reports by a factor of three. I went looking for headroom that was never there.
- 137 restarts in 11 hours. Memory was fine. It wasn't an OOM — my own liveness probe was killing the service because it couldn't answer `/health` under batch load. an other week lost for my enjoyable. 

All of it, and the rest, is in [agent-skills](https://github.com/CARL-Bouvet/agent-skills).
---

Based in France. I work in English and French.
