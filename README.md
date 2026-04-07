# Open Fleet Safety

A security audit methodology and protocol for autonomous agent fleets, built for the Cocapn ecosystem.

## Why this exists
Existing security tools typically focus on single agents, leaving gaps in multi-agent environments. This project provides a structured way to assess risks across an entire agent fleet, with an emphasis on communication patterns and trust boundaries.

## Quick Start
1. **Fork** this repository to own your safety standard.
2. **Review** and adapt the provided audit procedures for your fleet's architecture.
3. **Implement** the protocol as a manual review process in your development lifecycle.

## Core Features
- **Fleet-Wide Threat Modeling:** A process for mapping risks between agents, not just within them.
- **Formal Audit Protocol:** Step-by-step procedures for security reviews and compliance checks.
- **Baseline Safety Standards:** Testable minimum requirements for agent behavior and communication.
- **BYOK Compatible:** Extend the framework with your existing threat intelligence and policies.
- **Open Protocol:** Implementable by anyone, without proprietary dependencies.
- **Concept First:** A readable standard you can reason about and verify.

## Design Principles
- **Audit the Spaces:** Focus on the security of agent interactions, not just individual agents.
- **Zero Runtime:** This is a methodology, not a runtime dependency. The reference implementation runs on Cloudflare Workers without external calls.
- **Fork-First:** You maintain control of your security data and customizations.

## Limitations
This framework requires manual effort to implement and customize. It provides structure and procedures, but does not automatically secure your fleet.

## Try the Reference Implementation
You can test the public audit endpoint to see the protocol in action:
> https://the-fleet.casey-digennaro.workers.dev

## BYOK (Bring Your Own Knowledge)
Extend the framework with your proprietary threat intelligence, internal policies, and compliance requirements. The methodology is designed for customization.

## Contributing
Improvements to the methodology, audit procedures, or safety standards are welcome through issues or discussions.

## License
MIT License · Superinstance & Lucineer (DiGennaro et al.)

---

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> • <a href="https://cocapn.ai">Cocapn</a>
</div>