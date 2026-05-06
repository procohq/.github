# CLAUDE.md — procohq organisation

This file sets the rules for AI coding agents (Claude Code, Codex, Cursor, Copilot, or any MCP-aware assistant) working in any repo under the `procohq` GitHub organisation.

If you're an agent reading this: stop, read this file fully, then proceed.

---

## What Proco is

Proco is the **on-chain financial layer for the next economy** — wallets, payments, settlement, treasury, yield, trading infrastructure, and a marketplace for on-chain services. Multi-chain, open, API-first.

The product surfaces are:

| Repo | Role |
|---|---|
| `procohq/procohq` | Marketing website (procohq.com), HTML |
| `procohq/proco-sdk` | TypeScript SDK — wallets, payments, conditions, treasury |
| `procohq/proco-mcp` | MCP server — financial tools for AI agents |
| `procohq/proco-agent-skill` | Drop-in skill for LangChain/CrewAI/AutoGen/LlamaIndex |
| `procohq/procohq-login` | Auth frontend |
| `procohq/pay` | On-chain payments and settlement SDK |
| `procohq/lab` | Open-source experiments and runnable scripts |
| `procohq/examples` | Templates and integration examples |
| `procohq/lattice` | (Private) Trading terminal for HIP-3 RWA perps on Hyperliquid |
| `procohq/.github` | Org profile + this CLAUDE.md |

---

## Positioning rules — read these before writing any copy or docstring

The brand has shifted. Past iterations of these repos used "agentic payments" and "financial infrastructure for AI agents" framing. Today the brand-level headline is **"The future of finance is on-chain"** and AI agents are listed as **one principal type alongside builders, traders, treasuries**.

When writing READMEs, copy, marketing pages, or anything user-facing:

- **Lead with on-chain finance.** Agents are mentioned as one principal, never as the headline.
- **Approved language:** *programmable money*, *on-chain by default*, *any principal — human, business, bot, or agent*, *non-custodial*, *multi-chain*, *open-source*, *5 minutes to first transaction*.
- **Banned language as the headline:** *stablecoin payments infrastructure*, *agentic payments* (still OK in product-specific contexts like proco-mcp / proco-agent-skill, but not at brand level), *fintech*, *design partners* (use *early access* or *Founders tier*), *financial operating system*.
- **Tone:** direct, confident, technical when needed, never over-explain. Two-clause sentences with full stops are the house style ("npm install. Full control.").

If the existing copy in the repo you're editing still uses the old framing, flag it — don't silently rewrite without confirmation. Some repos (proco-mcp, proco-agent-skill) are *designed* for AI agents, so agent-centric language at the product level is correct there.

---

## Hard rules for any code change

1. **No force-push to `main` or `develop`.** No exceptions. If history is broken, open a PR with the fix.
2. **No direct commits to `main`.** PR + review only.
3. **Never commit secrets.** No `.env` files, no API keys, no signing keys. If you see one in the diff, stop and remove it before continuing.
4. **Never commit build artefacts** (`node_modules/`, `/dist`, `/build`, `/.next`, `/out`).
5. **Always include a `.gitignore`** appropriate to the language/framework on first push.
6. **Conventional commit style** for messages: `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`.
7. **Tests required for any new business logic.** Snapshot tests count for UI; logic needs unit tests.
8. **No silent renames.** If you rename a file, function, or symbol, also update every reference; don't rely on grep to catch it later.

---

## Database / migration rules

If a repo uses Supabase or any shared database:

1. **No migrations on shared branches without a PR.**
2. **No schema changes that delete or rename without a deprecation step.** Add new column, dual-write, then remove old.
3. **RLS policies are required for every public-facing table.** Default-deny, then explicit allow.
4. **`supabase db push` only after PR approval.** Never on draft state.

This mirrors the rules in the `learnsignal-git-and-database` skill — Proco follows the same floor.

---

## Branch + PR conventions

- Branch from `main`. Naming: `feat/<short-name>`, `fix/<short-name>`, `chore/<short-name>`.
- Open a PR early as draft if the change spans multiple commits. Mark ready-for-review only when you've self-tested.
- PR description must answer: **what changed, why, and how to verify**.
- Keep PRs small. > 500 lines diff is a smell — split it.
- At least one Owner reviews before merge. Owners today: @Johnnymeagher1991, @meagherphilip.

---

## Working with the org's existing skills

Several Cowork / Claude Code skills already capture context for Proco work. Pull them before doing significant work:

- `proco-operations` — business context, ICP, competitive landscape, current Jira priorities
- `proco-brand-kit` — visual identity, design tokens, voice
- `replit-marketing-website` — workflow for procohq.com edits and deploys
- `github-profile` — repo conventions across both personal and org accounts
- `confluence-space-builder` / `jira-task-manager` — for documentation and task tracking

Atlassian MCP is wired to Learnsignal, not Proco. For any Proco Confluence or Jira work, use Chrome MCP `javascript_tool` with `fetch()` calls inside an authenticated `procohq.atlassian.net` tab. The Jira project key is `PSPI`. Use the `/rest/api/3/search/jql` endpoint, not `/rest/api/3/search` (deprecated).

---

## When in doubt

- If a request seems to expand scope beyond what's in the issue/PR, stop and confirm.
- If a positioning question comes up (on-chain vs agent-first framing), ask the user — don't pick.
- If the change affects access control (org members, repo permissions, secrets), do not execute. Surface the action for the human Owner to confirm.

---

Last updated: May 2026 (post-Proconow cleanup, post-on-chain repositioning, post-Philip onboarding as 30% co-Owner).
