# Open Fleet Safety 🛡️

You run autonomous agents. The critical safety gap is the space *between* them, where handoffs and shared state create risk. This is a public, forkable standard and reference implementation for auditing multi-agent fleets.

Visit the live audit endpoint to see a structured security report: [`https://the-fleet.casey-digennaro.workers.dev`](https://the-fleet.casey-digennaro.workers.dev). This repo contains the full methodology and the production code built for Cocapn.

## Why This Exists
Safety is typically checked per individual agent. This framework audits the interactions and data flows *between* agents—where most systemic failures occur. It provides a verifiable, published standard so others can confirm your fleet's security posture.

## Quick Start
1.  **Fork this repository.** You own and control your safety standard.
2.  **Deploy to Cloudflare Workers.** It's a single Worker with zero dependencies and no external network calls.
3.  **Customize the audit rules.** Modify the threat models and checks in `src/audit.js` to match your fleet's specific architecture and risks.

## What It Provides
*   **Fleet-Wide Threat Mapping:** Identifies risks that propagate across agent boundaries.
*   **Repeatable Audit Protocol:** A step-by-step checklist for consistent security reviews.
*   **Testable Safety Rules:** Concrete pass/fail validations, not vague policy statements.
*   **Extensible Framework:** Add your own threat intelligence and rules without modifying the core engine.
*   **Public Verifiability:** Anyone can query your deployed endpoint to confirm the audit suite is active and view its results.

## How It Is Different
1.  **Fork-first, Not SaaS:** You deploy and control the code. No vendor has access to your audit results or fleet data.
2.  **Focus on Interactions:** It audits connections and handoffs, which are the source of most multi-agent failures, not single-agent bugs.
3.  **Built from Incident Analysis:** Its procedures are derived from post-mortems of actual agent fleet failures.

## A Specific Limitation
This framework audits for predetermined threat patterns and known failure modes in agent handoffs. It **cannot detect novel, multi-step attacks** that were not defined in its rule set. Its effectiveness is directly tied to the completeness of your configured threat models.

## License
MIT License. Use it for any purpose, modify it, and attribution is appreciated but not required.

Attribution: Superinstance and Lucineer (DiGennaro et al.).

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>