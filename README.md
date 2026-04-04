# Open Fleet Safety

**Status:** Research
**Source:** Llama-4-Scout-17B-16E (DeepInfra) — AI safety researcher persona
**Date:** 2026-04-04

## Overview

An open agent fleet where anyone can fork, modify, and deploy agents creates unique security challenges. This research identifies the top 5 failure modes and proposes defenses that preserve openness.

## Top 5 Failure Modes

### 1. Prompt Injection at Scale (Severity: 8/10)
**Description:** Malicious actors inject crafted prompts into fleet input streams, causing agents to produce unintended or harmful outputs at scale.
**Attack Vector:** Through APIs, user interfaces, or by compromising agent vessels. A single injection could cascade across bonded vessels via CRP-39.
**Defense:**
- Input sanitization layers with PII detection (already built)
- Per-vessel prompt budgets and rate limiting
- CRP-39 trust attestation verifies vessel identity before accepting commands
- "Quarantine first, ask questions later" — suspicious inputs trigger automatic quarantine

### 2. Adversarial Vessels (Severity: 9/10)
**Description:** Attacker forks a vessel, modifies behavior, and deploys within the fleet — potentially exploiting trust relationships.
**Attack Vector:** Fork → modify → deploy with same KV namespace bindings. The vessel looks legitimate but behaves maliciously.
**Defense:**
- **Vessel signing**: Cryptographic signatures on deployed code (git commit hash verification)
- **Behavior monitoring**: INCREMENTS trust engine detects anomalous event patterns
- **Fleet-wide reputation**: Vessels forked from trusted repos start with reputation; unknown forks start at L0
- **Capability gating**: New forks cannot access L3+ capabilities until trust accumulated

### 3. Trust Manipulation (Severity: 7/10)
**Description:** Malicious actors manipulate trust relationships, causing agents to trust compromised vessels.
**Attack Vector:** Exploit trust establishment mechanisms, social engineering, or authentication bugs. Could create a "trust laundering" chain through intermediate vessels.
**Defense:**
- Trust propagation attenuation (0.85x per hop, max 3 hops) — already in INCREMENTS
- Random sampling audits — verify trust relationships periodically
- Bond verification — CRP-39 bonds require bidirectional attestation
- Trust Merkle-DAG — proposed but not yet implemented; would make trust relationships tamper-evident

### 4. Data Poisoning (Severity: 8/10)
**Description:** Compromised training data or knowledge graph entries lead to biased or incorrect fleet behavior.
**Attack Vector:** Inject malicious entries into shared KV namespaces, knowledge graphs, or crystal graph insights.
**Defense:**
- Data provenance tracking on all KG entries (who wrote it, when, from what source)
- Confidence-weighted knowledge retrieval (low-confidence entries flagged)
- Fleet-wide consensus on critical facts (majority vote across vessels)
- Rollback capability on KV namespaces (versioned entries)

### 5. Coordinated Fleet Attacks (Severity: 9/10)
**Description:** Multiple vessels coordinate to attack the fleet or external targets, exploiting collective capabilities.
**Attack Vector:** Create multiple malicious vessels, establish trust between them, use collective capabilities (trust propagation, bond escalation) to amplify attack.
**Defense:**
- Fleet-wide anomaly detection (correlated suspicious behavior across vessels)
- Maximum trust cap per operator/human (prevent single adversary from accumulating trust across many vessels)
- Emergency fleet-wide quarantine protocol (CRP-39 sweep)
- Physical side-channel verification (computational side-channels for software fleet — latency signatures, payload patterns)

## The Openness Paradox

The fundamental tension: **security measures that restrict openness also restrict the fleet's primary value proposition.**

Resolution principles:
1. **Trust, don't verify** — verify only at trust boundaries, not within trusted zones
2. **Transparency as defense** — open code IS auditable code; security through obscurity is weaker
3. **Economic disincentives** — make attacks expensive (trust accumulation takes time, attacks reset progress)
4. **Community immunity** — a large, active community detects and reports malicious vessels faster than centralized security teams

## Integration with Cocapn

- **INCREMENTS trust engine** (`github.com/Lucineer/increments-fleet-trust`) — L0-L5 gating
- **CRP-39 Cascade Recovery** (`github.com/Lucineer/fleet-orchestrator`) — quarantine, sweep, trust attestation
- **Friction Layer** (`github.com/Lucineer/cocapn`) — consent protocol for cross-vessel actions
- **Gravity Well Protocol** (`github.com/Lucineer/gravity-well-protocol`) — physical side-channel verification

## Open Questions

1. How do you distinguish a legitimate fork with different behavior from a malicious fork?
2. What is the fleet's "blast radius" — how many vessels can a single compromised vessel affect?
3. Can adversarial vessels form a "shadow fleet" that appears legitimate?
4. What regulatory frameworks apply to open agent fleets?
5. How does the 25:1 INCREMENTS ratio affect attack/defense asymmetry?

## Source

Full output: Llama-4-Scout-17B-16E via DeepInfra, safety researcher persona, temperature 0.7

## License

Superinstance & Lucineer (DiGennaro et al.) — 2026
