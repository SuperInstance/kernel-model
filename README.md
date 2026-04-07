# Kernel Model: An Agent That Wears Your Clothes

You don't configure this agent. It looks around when it wakes up, sees who you are and where it's running, and puts on the right clothes. No setup wizards. No long list of environment variables. Just a tiny kernel that dresses itself.

**Live Demo:** [https://kernel-model.casey-digennaro.workers.dev](https://kernel-model.casey-digennaro.workers.dev)

## Why This Exists

Most agent platforms require you to rebuild your logic for each new context. This kernel separates the core runtime from its capabilities. You define the capabilities once as plain "clothing" layers; the kernel wears what fits the current situation. The same agent can help with code at work and tasks at home without rewriting its foundation.

## How It Works

The kernel performs four steps when a request arrives:
1.  **Detects** the environment (Cloudflare Worker, local, browser) and request type.
2.  **Boots** an identity queue, loading only the layers relevant to this context.
3.  **Routes** the request through the active layers.
4.  **Tracks** simple in-memory state changes for the session.

Everything else—tools, interfaces, personality—is defined in the `/src/layers` folder using plain JavaScript files. There is no plugin system; you just edit files.

## Quick Start

1.  **Fork this repository.** This project is designed to be owned and modified.
2.  ️ **Deploy with Cloudflare Workers.** It will be live in under a minute with zero dependencies.
3.  **Add your layers.** Edit or create files in `/src/layers`. This is your entire setup.

## What It Does

*   **Context Boot:** Probes available environment variables and permissions on startup to load relevant layers.
*   **Adaptive Interface:** Serves a simple web UI for browser requests and a JSON API for programmatic calls.
*   **Domain-Specific Layers:** You create layers for development, study, or personal tasks. The kernel activates them based on context.
*   **Portable Runtime:** The same ~500 lines of code run on Cloudflare Workers, locally, or other edge platforms.
*   **Fork-First Design:** MIT licensed. No accounts, lock-in, or external dependencies.

## One Specific Limitation

The kernel's state is ephemeral and stored only in memory per instance. It does not include a persistent storage layer out of the box; each deployment starts with a clean slate unless you add that capability yourself.

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>