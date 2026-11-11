# Carl Bouvet

Full-stack JavaScript engineer. Node/Bun back ends, Nuxt front ends, and the Docker Swarm and k3s clusters they actually run on. Seven years of JavaScript, working solo — which means I own the whole chain, from the query to the 3am incident.

My public work lives in three repositories:

- **[Coati](https://github.com/CARL-Bouvet/coati)** — an assistant in your browser's side panel that runs on your own AI model, local or online. The API keys stay in a small local program and never reach the extension or the pages you visit.
- **[resilient-ws](https://github.com/CARL-Bouvet/resilient-ws)** — a dependency-free WebSocket client that detects the socket which stays open and silently stops delivering, extracted from my own ingestion stack.
- **[agent-skills](https://github.com/CARL-Bouvet/agent-skills)** — production knowledge distilled from real postmortems, packaged for AI coding agents. Every rule in it cost me hours or days to learn.

### What I actually do

**WebSocket ingestion that survives production.** I ingest live trades from about ten crypto exchanges. Connecting was never the hard part — the hard part is the socket that stays open while silently delivering nothing. Application-level ping/pong on top of the transport, zombie detection, clean reconnect with no orphaned timers. I extracted that invariant and published it: **[resilient-ws](https://github.com/CARL-Bouvet/resilient-ws)** — including the case where the rule inverts, and why CCXT Pro does not catch this failure.

**An AI model inside a product, without handing out the keys.** Coati's browser extension holds no secret. A local program, reachable only on `127.0.0.1` and paired with the extension through an authenticated handshake, keeps the keys and talks to Ollama, LM Studio, Claude or any OpenAI-compatible service. Installers for Linux, macOS and Windows, CI on all three, and the threat model and design decisions are published in the repository.

**Data at scale, and the ways it breaks.** MongoDB in depth: index-first with `.explain()`, grouped writes, the TTL that silently no-ops because the field isn't a `Date`, the engine cache that fights the container's memory cap. I've paid for each of those in production.

**Infrastructure I run myself.** Docker Swarm, then a single-node k3s cluster in real production — ingress reachable only through a WireGuard tunnel, CronJob backups, a dead-man's switch, reboot-durability tested live. I host what I ship and keep it alive.

**Vue and Nuxt, plus Three.js when the interface needs 3D** — including the Blender side: glTF import, cleanup and re-export, Draco compression, and why your scene is slow. I shipped a browser game for a paying client.

### Not my ground

AWS, GCP, Firebase, Supabase. Managed cloud isn't where I work, and I'd rather tell you that now than learn it on your budget.

### Things I learned the expensive way

- A MongoDB TTL index on `Date.now()` does nothing. No error, no log. 127 GB and two months of work, gone. Not my first scar — but a good one.
- `kubectl top` under-reports by a factor of three. I went looking for headroom that was never there.
- 137 restarts in 11 hours. Memory was fine. It wasn't an OOM — my own liveness probe was killing the service because it couldn't answer `/health` under batch load. Another week gone for my delight.

All of it, and the rest, is in [agent-skills](https://github.com/CARL-Bouvet/agent-skills) and [resilient-ws](https://github.com/CARL-Bouvet/resilient-ws).

---

Based in France. I work in English and French — I write English a good deal better than I speak it, so written and async collaboration suits me best.

**Available for freelance work, remote.** Back ends and ingestion pipelines, AI model integration, MongoDB, self-hosted infrastructure. The write-up behind `resilient-ws` is [here](https://dev.to/carlbouvet/my-websocket-was-open-the-whole-time-it-just-stopped-sending-anything-140e).

Reach me at **carlbouvetdev@gmail.com** or on [LinkedIn](https://www.linkedin.com/in/carl-bouvet-dev/).
