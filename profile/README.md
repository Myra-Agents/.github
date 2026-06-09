<div align="center">
  
# ![Myra Agents logo](https://github.com/Myra-Agents/.github/blob/main/banner.png?raw=true)

**Manage & Run your AI Agents from anywhere.**

🌐 **[myra-agents.github.io](https://myra-agents.github.io)**

Drop a prompt on a card, launch it, and Myra spawns a configured AI agent
(opencode · copilot · claude · custom) in headless mode and streams its
output back onto the board. Cards flow **Draft → Todo → In Progress → Waiting
Feedback → Awaiting Review → Done**. Schedules auto-materialize and launch cards
on a cron / daily / weekly / interval basis.

*Myra* is Swedish for **ant** — build your colony of Agents and achieve your goals.

</div>

---

## Repos

| Repo | What it is | |
|------|------------|---|
| **[Myra-Agents](https://github.com/Myra-Agents/Myra-Agents)** | The desktop app — a Kanban board that runs CLI agents. **Next.js 16 + Tauri v2 (Rust).** | 🌐 |
| **[Pheromones](https://github.com/Myra-Agents/Pheromones)** | `@myra/shared` — TypeScript types, API contracts, pure domain helpers. | 🌐 |
| **[Plugins](https://github.com/Myra-Agents/Plugins)** | Runtime plugins over a language-agnostic subprocess protocol — agent providers + event reactions. | 🌐 |
| **[Myrastack](https://github.com/Myra-Agents/Myrastack)** | One-command multi-repo dev workspace bootstrap. | 🌐 |
| **Worker** | The app's prebuilt backend binary. | 🔒 |
| **Nest** | Managed cloud service. | 🔒 |

<sub>🌐 public · 🔒 private</sub>

## How it fits together

```mermaid
flowchart LR
  app["Myra-Agents\n(Next.js + Tauri)"]
  worker["Worker\n(prebuilt binary)"]
  plugins["Plugins\n(subprocess protocol)"]
  shared["Pheromones\n(types + contracts)"]
  nest["Nest\n(managed cloud)"]
  remote["Remote agents\n(self-hosted)"]

  app -->|spawns & supervises| worker
  worker -->|loads| plugins
  app -.->|optional| nest
  nest -.->|brokers| remote
  app -.->|shared types| shared
```

The desktop app ships with a **prebuilt Worker binary** — so you can build
and run the whole app from open source, no extra access needed.

## Quick start

One command — clones every repo, wires it up, installs deps:

```bash
curl -fsSL https://raw.githubusercontent.com/Myra-Agents/Myrastack/develop/install.sh | bash
```

Then run the app:

```bash
cd ~/Myrastack
./dev.sh sidecar      # fetch the prebuilt Worker binary
./dev.sh app          # run the desktop app
```

See **[Myrastack](https://github.com/Myra-Agents/Myrastack)** for the
full workspace setup.

## Extend it

Plugins extend the app without touching its core, over a small contract (a
`manifest.json` + stdin/stdout NDJSON):

- **Agent providers** — contribute agents to the card picker.
- **Event reactions** — react to board events (Slack, webhooks, integrations…).

Start from **[Plugins](https://github.com/Myra-Agents/Plugins)**
(`PROTOCOL.md` + JSON schema + examples).

## Contributing

All repos follow **GitFlow-lite**: branch off `develop`, PR back into `develop`;
`main` is release-only. Conventional Commit subjects. Each repo carries a
`CLAUDE.md` with its build/run/convention notes.

---

<div align="center">
<sub>Made with Kanban, coding agents, and a lot of streamed stdout.</sub>
</div>
