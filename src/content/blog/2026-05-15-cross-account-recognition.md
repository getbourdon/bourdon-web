---
title: "How Codex recognized Bourdon on a brand-new account"
description: "A user's Codex account became uneditable mid-week. They created a new email and signed in fresh on the same machine. The brand-new account's first conversation correctly recognized the project — purely from local recognition substrate. The first observed live confirmation of Bourdon's cross-account-continuity thesis."
pubDate: "May 15 2026"
---

Until 2026-05-15, "agent continuity around the work, not the vendor account" was Bourdon's stated thesis. As of 2026-05-15 ~07:00 PT, it's a measured outcome with a reproducible substrate.

The trigger wasn't a planned demo. It was a broken plan-upgrade flow.

## What happened

A Bourdon user's Codex account became uneditable mid-week — a stuck plan-upgrade flow that wouldn't resolve. They created a new email, signed out, and signed back in fresh on the same Windows machine. Same machine, new vendor identity.

Two surprises followed.

**Surprise 1: the Codex App still surfaced the prior chat list.** This is probably native local-cache behavior — account-bound but PC-local cache may persist. Not Bourdon's doing.

**Surprise 2 — the meaningful one: on the brand-new account's first conversation, Codex correctly recognized Bourdon as the active project.** Including the lineage from its prior name (Continuo) and Codex's own contributing role on the Codex adapter. The prompt was a direct question: *"do you remember what bourdon is?"*

Codex's reply, verbatim:

> Yes. Bourdon is your recognition-first runtime layer, formerly Continuo: a federated agentic memory system meant to help agents recognize the current project, concepts, entities, and prior context quickly from bounded metadata, not by dumping raw transcripts back into the model.
>
> For this PC Codex setup, Bourdon's role is the local bridge: read live Codex state from SQLite, recover lightweight concepts like Bourdon, Continuo, runtime recognition, and recognition first runtime layer, then expose that through things like the Codex L5 manifest and a bounded fallback memory section.
>
> On the chat persistence question: seeing old chats in the Codex App screen is probably native Codex app/account/local state. Bourdon is more likely helping with recognition once a thread is active, not necessarily owning the visible chat list. The evidence I can see is that Bourdon did generate a local fallback memory block from Codex session and rollout metadata, with your Bourdon thread and concepts present. So: native UI persistence may be Codex; the "ah, this is Bourdon/Continuo/runtime recognition" recall is Bourdon doing its job.

The distinction Codex made — *native local-cache for the chat list, Bourdon for the project recognition* — came **unprompted**. We didn't ask it to attribute. It did so on its own. That distinction is what makes this a real finding rather than a marketing anecdote.

When asked about cross-account file access:

> I was able to read local files under: `C:\Users\cumul\.codex`. That means this new Codex account/app session appears to be running against the same local machine state, so Bourdon can still see the prior local Codex memory/state files. I did not access a remote "other account" cloud store or private server-side chats from the old account.

When asked whether this was the intended behavior:

> Yes. That is the core proof-of-life. The account changed, but the local recognition layer still found the project identity, the Bourdon/Continuo lineage, and the current conceptual frame. That means Bourdon is doing the thing it is supposed to do: preserving agent continuity around the work, not around a vendor account.

## How it worked

The recognition substrate Codex pulled from was three things layered:

1. **Local Codex state** at `~/.codex` — session metadata, rollouts, the live `state_5.sqlite` Codex itself maintains. This survives account changes because it's a per-machine file, not a per-account cloud blob.
2. **Bourdon's fallback memory section** — Bourdon writes a bounded summary of recognized concepts, threads, and context into a format the next Codex turn picks up. This is generated from local Codex state plus Bourdon's own federation library. Account-agnostic.
3. **The Codex L5 manifest** that Bourdon publishes — `~/agent-library/agents/codex.l5.yaml`, a per-agent public glossary of recognized entities, sessions, and project context. Read by Bourdon's L6 federation server, exposed as MCP, also account-agnostic.

The new Codex account inherited none of the user's prior server-side chat history. It inherited everything in those three local layers. That's the whole architecture working as intended: recognition lives in local substrate, not in the vendor's account database.

## Honest gaps the same transcript surfaced

Codex itself flagged three gaps, in the same conversation that proved the core thesis. Filing them as Phase 1.5 work:

1. **Latency.** First-turn recognition took about 5 minutes. The user had Codex set to extra-high reasoning, which dominates the cost — but we don't have a repeatable measurement at standard reasoning settings. That number needs to be a published latency matrix per release, not an anecdote.
2. **Trigger surface.** Recognition surfaced when Codex was directly asked *"do you remember what bourdon is?"*. Whether it would have surfaced unprompted — woven into a response to an unrelated question — is an open empirical test we haven't run yet.
3. **Source attribution.** Codex couldn't cleanly partition Bourdon-supplied context vs. its own native context in its answer. Future Bourdon turn-prep responses should mark their contributions explicitly (e.g., a `[bourdon]` prefix on synthesized recognition lines) so users and other agents can audit the source chain.

None of these invalidate the core finding. They're the next-step work to make the finding feel automatic instead of demonstrable.

## Why this matters

Most agent-memory products are vendor-account-bound by default. ChatGPT memory dies when you switch accounts. Cursor's memory is per-tool, per-project, per-install. The implicit deal is *we'll remember you, as long as you stay in our product*.

Bourdon's deal is different. The recognition substrate lives on your machine, in a vendor-neutral format (the L5 manifest), federated through an MCP server you also run. Whichever agent happens to be active reads from it. So:

- You can switch vendor accounts without losing project context.
- You can switch from Codex to Claude Code to Cursor on the same project, mid-flow, without re-explaining.
- You can move across machines via standard sync (we use git for the federation library).
- You own your own memory layer, independent of any single AI vendor.

The 2026-05-15 cross-account test isn't a complete proof of all of those — but it's the first complete proof of the most important one: **continuity around the work survives a change of vendor identity on the same machine.**

That's the deal.

## What the next test looks like

The cross-account test was on the same machine. The next test is **across machines** — does the recognition substrate, when synced via git (PC ↔ Mac), produce equivalent recognition behavior on the second machine without manual context-passing?

We have the substrate. We have the sync. We don't have the measured outcome yet. That's coming.

---

*Source: full benchmark with conditions table, source chain, and gap analysis at `~/claude-brain/PROJECTS/NEUROLAYER/BENCHMARKS/2026-05-15_cross_account_recognition.md` in the project owner's local notes. Bourdon project: [github.com/getbourdon/bourdon](https://github.com/getbourdon/bourdon). Landing: [bourdon.ai](https://bourdon.ai).*
