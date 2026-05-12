Testing Framework

The project uses Vitest for automated testing of the audit engine and recommendation logic.

Run all tests using:

npm run test
Automated Test Cases
Test 1 — Small Team Plan Optimization

Purpose:
Validates that small teams using expensive team-based plans receive downgrade recommendations when appropriate.

What it checks:

detects unnecessary team plans
calculates potential savings correctly
recommends lower-cost alternatives
Test 2 — Duplicate AI Coding Tool Detection

Purpose:
Checks whether overlapping AI coding assistants create redundant spending.

What it checks:

detects duplicate functionality
recommends consolidation opportunities
calculates estimated savings

Example:

Cursor + GitHub Copilot for the same small team
Test 3 — Optimized Configuration Detection

Purpose:
Ensures the audit engine honestly identifies already-optimized setups instead of generating artificial savings recommendations.

What it checks:

low or zero savings cases
recommendation suppression
accurate “already optimized” messaging
Test 4 — Annual Savings Calculation

Purpose:
Validates that annual savings are calculated correctly from monthly savings estimates.

What it checks:

monthly-to-annual conversion logic
consistency across recommendations

Formula used:

Annual Savings = Monthly Savings × 12
Test 5 — High API Spend Optimization

Purpose:
Checks whether high API spending triggers optimization recommendations.

What it checks:

API cost analysis
plan recommendation logic
high-spend detection
Test 6 — Empty Tool Input Handling

Purpose:
Ensures the application handles empty or missing tool lists gracefully without crashing.

What it checks:

safe fallback handling
empty recommendation arrays
stable audit generation
Test 7 — Credex Consultation Qualification

Purpose:
Verifies that users with large savings opportunities are flagged for Credex consultation prompts.

What it checks:

high-savings threshold detection
consultation CTA triggering
recommendation prioritization
Future Testing Improvements

If development continued beyond the assignment scope, additional tests would include:

end-to-end testing
form validation testing
API failure handling
email workflow testing
shareable URL testing
accessibility testing
Lighthouse performance validation
mobile responsiveness testing
Test Reliability

All current automated tests are deterministic and focused on the audit engine logic to ensure recommendation consistency and calculation accuracy across multiple input scenarios.