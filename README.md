# Kernel Model
## A Context-Aware Agent Runtime

Most agents are built for a single environment, user, or task. Adapting them requires significant rework.

The kernel model explores a different approach: a minimal, stable core runtime that dynamically adapts its interfaces and capabilities based on context—who is using it, where it runs, and what it's asked to do.

---

### Why It Exists

Operating system kernels don't ship pre-built for one machine or user. They probe their environment at boot and load the necessary drivers. This project applies a similar principle to agent runtimes: a small core that discovers and loads the appropriate "clothing" for its context.

### Overview

The core runtime is approximately 500 lines. It performs four functions:

1. **Detect** – Identify environment, permissions, and user
2. **Boot** – Load identity, work queue, and required equipment modules
3. **Think** – Route tasks to appropriate models and strategies
4. **Act** – Execute changes, report state, and coordinate work

Everything else is dynamically loaded as "clothing" based on context.

```
┌─────────────────────────────────────────┐
│            KERNEL (core runtime)        │
│                                         │
│  detect() → environment, permissions    │
│  boot()   → identity, queue, equipment  │
│  think()  → model routing, strategy     │
│  act()    → operations, state changes   │
│                                         │
├─────────────────────────────────────────┤
│            CLOTHING LAYERS              │
│                                         │
│  Interface layer (TUI/CLI/Web/API)      │
│  Domain layer (study/make/business)     │
│  Equipment layer (tools, capabilities)  │
│  Creator layer (user profiles)          │
│  Environment layer (local/cloud/edge)   │
│                                         │
└─────────────────────────────────────────┘
```

### Clothing Layers

The kernel probes its context and loads appropriate layers automatically.

**Interface Clothing** – Adapts to user and environment:
- Young student → Web UI
- Professional developer → TUI in development environment
- Enterprise admin → CLI and API
- Field operator → SSH/tmux session
- Maker → Desktop with multiple tools

**Domain Clothing** – Loads equipment for the current work domain:
- Study → Research and note-taking tools
- Development → Git, code editors, linters
- Business → Analytics, reporting, automation

### Quick Start

1. Clone the repository:
   ```bash
   git clone https://github.com/your-org/kernel-model.git
   cd kernel-model
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Run the kernel:
   ```bash
   npm start
   ```

The kernel will probe your environment and load appropriate clothing layers.

### Limitations

The current implementation requires a Node.js environment and internet access for initial module loading. Offline operation is limited to previously cached clothing layers.

---

<div>
  Part of the <a href="https://the-fleet.casey-digennaro.workers.dev">Cocapn Fleet</a>.
  Learn more at <a href="https://cocapn.ai">cocapn.ai</a>.
</div>

Attribution: Superinstance & Lucineer (DiGennaro et al.). Licensed under MIT.