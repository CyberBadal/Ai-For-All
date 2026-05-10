# Pricing Data Registry & Audit Logic Rules

This file serves as the single source of truth for the Audit Engine's calculations. It contains the retail pricing for common AI tools and the logic used to identify "waste."

## 1. Tool Pricing Matrix (Retail)

| Tool | Plan | Monthly Cost | Per Seat | Key Features / Limits |
| :--- | :--- | :--- | :--- | :--- |
| **ChatGPT** | Plus | $20 | No | Individual use |
| **ChatGPT** | Team | $30 | Yes | 2-seat min, admin console |
| **ChatGPT** | Enterprise | ~$60 | Yes | Variable, SOC2, SSO |
| **Claude** | Pro | $20 | No | Individual use |
| **Claude** | Team | $30 | Yes | 5-seat min |
| **GitHub Copilot** | Individual | $10 | No | Individual use |
| **GitHub Copilot** | Business | $19 | Yes | Policy management |
| **Cursor** | Pro | $20 | No | Individual, 2000 fast completions |
| **Cursor** | Business | $40 | Yes | Centralized billing, privacy mode |
| **v0.dev** | Premium | $20 | No | Higher generation limits |

## 2. API Pricing (Average Usage Tiers)

To simplify the audit for non-technical users, we categorize API spend into "Usage Profiles":
* **Light:** $10–$50/mo (Testing, occasional tasks)
* **Moderate:** $50–$500/mo (Production startup, medium volume)
* **Heavy:** $500+/mo (Scaling product, high-frequency LLM calls)

## 3. Recommendation Logic Rules

The Audit Engine (`engine.ts`) evaluates user input against these specific "Waste Signatures":

### Rule A: The "Ghost Town" Team Plan
* **Trigger:** User has a `Team` plan for ChatGPT or Claude but only `1` seat active.
* **Logic:** `if (seats < 2 && plan === 'Team')`
* **Recommendation:** Downgrade to `Pro/Individual`.
* **Annual Saving:** ~$120.

### Rule B: Redundant Coding Assistants
* **Trigger:** User pays for both `GitHub Copilot` AND `Cursor Pro`.
* **Logic:** `if (hasTool('Cursor') && hasTool('Copilot'))`
* **Recommendation:** Consolidate to one. Cursor's built-in models often replace the need for the standalone Copilot extension.
* **Annual Saving:** ~$120–$240.

### Rule C: The "Pro-User" Consolidation
* **Trigger:** Heavy spend on multiple individual LLM interfaces (Claude + ChatGPT + Perplexity).
* **Logic:** `if (toolCount > 3 && totalSpend > 60)`
* **Recommendation:** Use an aggregator like **Poe** or **OpenRouter** for specialized tasks, or pick one "Main" driver to reduce cognitive and financial overhead.

### Rule D: Credit Opportunity (The Credex Lead)
* **Trigger:** Total monthly spend > $500.
* **Logic:** `if (totalSpend > 500)`
* **Recommendation:** Apply for AI Cloud Credits. Startups can often get $1k-$25k in credits for OpenAI/Anthropic via partners.
* **Annual Saving:** $5,000+.

## 4. Calculation Methodology

1.  **Direct Waste:** The difference between current spend and the cost of the recommended optimized plan.
2.  **Redundancy Waste:** The total cost of a tool deemed unnecessary due to overlapping features.
3.  **Projected Annual Savings:** `(Monthly Savings * 12)`.
