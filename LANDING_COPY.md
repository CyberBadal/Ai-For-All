# SpendSentinel: Landing Page Overview
The goal of this page is to grab a founder’s attention in about 5 seconds. Most startups know they are wasting money on AI, but they’re too busy to go through their credit card statements. SpendSentinel does the boring work for them instantly.

## Why SpendSentinel stands out (Key Features)
The Overlap Detector: This is the most popular feature. It’s designed to find tools that do the same thing. For example, if your team is paying for both GitHub Copilot and Cursor, SpendSentinel flags it immediately so you can pick one and stop double-paying.

Real Startup Benchmarks: We don’t just guess if you're spending too much. We compare your stack against over $2.4M in real startup data. It tells you, "Hey, a startup of your size usually spends $X, but you're spending $Y," which makes the waste feel real.

The "Credex" Level-Up: This is our secret weapon. If we find that you're wasting a lot of money (over $500 every month), we don't just leave you there. We help you connect with Credex to get free AI credits or negotiate better deals that you couldn't get on your own.

Zero-Friction Sharing: We made the reports look really clean and professional. You get a unique link that you can just drop in Slack to show your co-founders or the board exactly where the money is going and how to fix it.

Simple "No-Login" Audit: Most tools make you sign up before you see anything. We flipped that. You get the value and see your savings first. We only ask for an email at the very end if you want to save the report or get the Credex help.

![alt text](<Screenshot 2026-05-12 205353.png>) ![alt text](<Screenshot 2026-05-12 205407.png>) ![alt text](<Screenshot 2026-05-12 205419.png>) ![alt text](<Screenshot 2026-05-12 205435.png>)


This is the core of the experience—the Audit Form. The UI you've built here is clean and focuses on making a boring task (data entry) feel fast and interactive.

Here is the overview for the SpendSentinel Audit Page written in a simple, human-focused way.

# Audit Page Overview
The Audit Page is where the "magic" happens. Instead of making users fill out a massive, intimidating spreadsheet, we’ve broken it down into simple, clickable tiles. It feels more like a quick quiz than a financial audit. This is key for SpendSentinel because we want founders to finish the process in under 2 minutes without getting bored or frustrated.

## Features of the Audit Flow
One-Tap Stack Building: Users don't have to type out their tools. They just tap the icons for the tools they use—like Cursor, Claude, or OpenAI. It’s visual, fast, and works perfectly on mobile if a founder is doing this on the go.

Contextual Deep-Dives: When you click a tool, a simple card pops up asking for the "must-have" info: your plan, your monthly spend, and how many seats you have. We intentionally kept this to just a few fields so we don't overwhelm the user.

The "Live Stack" List: As users add tools, they appear in a list at the bottom. This gives them a "running tally" of what they’ve entered. It feels satisfying to see the list grow and helps them double-check that they didn't miss anything before moving to the next step.

Smart Usage Categories: We ask what the tool is used for (like "Coding" or "Research"). This is the secret to our audit logic. If someone selects "Coding" for three different tools, SpendSentinel knows there’s a high chance of waste and can flag it in the final report.

Progress Persistence: Thanks to the Zustand setup, if the user accidentally closes the tab or their browser crashes while they are adding their 5th tool, everything stays saved. They can come right back and pick up exactly where they left off.

![alt text](<Screenshot 2026-05-12 205449.png>) ![alt text](<Screenshot 2026-05-12 205501.png>) ![alt text](<Screenshot 2026-05-12 205629.png>)![alt text](<Screenshot 2026-05-12 205638.png>)

# Results Page Overview

The Results Page is the "payoff" for the user. After they put in their data, we show them a polished dashboard that makes their spending easy to understand. The whole point is to take a messy list of subscriptions and turn it into a clear plan that saves them money. It’s designed to be simple enough to understand in one glance but detailed enough to share with a co-founder.

## Key Features

Smart Benchmarking: We use the company size and stage to show the user how their spending compares to other startups, so they know if their budget is normal or out of control.

The Spending Review: Before showing the final report, we give a clear summary of the total monthly cost. Seeing that big number in one place is usually a huge wake-up call for most founders.

Clear Action Cards: We don't use confusing financial talk. Each tool gets a simple "Keep" or "Remove" label with a short explanation of why it’s wasting money or how it overlaps with another tool.

Instant Savings Tags: Every suggestion has a bright green badge showing exactly how much money stays in their pocket each month. It makes the "win" feel immediate and easy to track.

Low-Friction Lead Capture: We show the value first, then offer a full PDF report via email. Since they’ve already seen the savings, they’re much more likely to give their email to get the details.

![alt text](<Screenshot 2026-05-12 205651.png>) ![alt text](<Screenshot 2026-05-12 205708.png>) ![alt text](<Screenshot 2026-05-12 205726.png>) ![alt text](<Screenshot 2026-05-12 205740.png>) ![alt text](<Screenshot 2026-05-12 205756.png>)
