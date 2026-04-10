## Proco

**Financial infrastructure for AI agents.**

Wallets · payment policies · programmable spending · agentic payments · agent-to-agent settlement · treasury — built for autonomous systems operating at machine scale.

### What we build

Proco gives AI agents their own financial identity. Every agent gets a non-custodial USDC wallet, programmable spending policies, and the ability to pay and get paid — without requiring a human in the loop.

- **Wallets** — provision agent wallets in milliseconds, with spending limits and automated top-ups
- - **Gateway** — accept payments from agents on any API, settled instantly in USDC
  - - **Conditions engine** — programmable payment policies: pay_when, pay_if, sweep_when, approval flows
    - - **x402 compatible** — native support for the machine-to-machine payment protocol backed by Coinbase, Google, Anthropic, Visa, and AWS
     
      - ### For developers
     
      - ```
        npm install @proco/sdk
        ```

        Drop Proco into any agent stack — TypeScript SDK, MCP server, or single-import Agent Skills for LangChain, CrewAI, AutoGen, and Claude Code.

        → [procohq.com](https://procohq.com) · [Docs](https://procohq.com/docs) · [Request early access](https://procohq.com/sign-in)
