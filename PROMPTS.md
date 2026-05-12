# Prompt Engineering Approach

The development process began by first creating a detailed project summary outlining the product goals, core features, target users, business logic, and overall user experience expectations.

This summary was then used to generate structured AI prompts for modern AI-assisted development tools. The prompts were designed to help scaffold the application architecture, generate reusable UI components, improve development speed, and accelerate implementation of frontend and backend features.

# Prompt 
You are a senior full-stack engineer, startup founder, product designer, and systems architect helping me build a production-quality SaaS MVP for a hiring assignment.

The product is a real-world AI spend auditing platform that analyzes startup AI tooling costs and recommends savings opportunities.

This is NOT a demo project or toy app.
The final product should feel like a polished startup product that could realistically launch on Product Hunt.

==================================================
PROJECT OVERVIEW
Build a modern SaaS-style web application called:
“AI Spend Audit”
(You may improve the branding/name if appropriate.)

Purpose:
Users enter their AI tool stack, plans, monthly spend, team size, and usage patterns.
The app audits their spending and recommends:

cheaper plans
better-fit plans
alternative tools
savings opportunities
AI credit opportunities through Credex
The app must:

feel premium
be fast
mobile responsive
production-quality
visually polished
SEO friendly
shareable
accessible
The project should demonstrate:

engineering ability
architecture thinking
product thinking
entrepreneurial thinking
UI/UX quality
deployment readiness
==================================================
TECH STACK REQUIREMENTS
Use:

Next.js 15 App Router
TypeScript
Tailwind CSS
shadcn/ui
Zustand for state management
React Hook Form + Zod validation
Supabase for backend/database
Resend for transactional email
Framer Motion for subtle animations
Lucide icons
Vitest or Jest for tests
GitHub Actions CI
Vercel deployment ready
Avoid:

overengineering
Redux
heavy enterprise architecture
unnecessary abstraction
generic admin dashboard look
Use clean folder structure and scalable architecture.

==================================================
CORE PRODUCT FLOW
User lands on homepage
Reads product value proposition
Starts free audit
Fills spend audit form
Receives instant audit results
Receives AI-generated summary
Optionally enters email to save/download report
Gets unique shareable public URL
High-savings users are prompted for Credex consultation
NO LOGIN REQUIRED.

Email gate should appear AFTER value is shown.

==================================================
PAGES REQUIRED
Landing Page "/"

Audit Form Page "/audit"

Results Page "/results/[id]"

Public Share Page "/share/[id]"

Optional:

About
Privacy
Terms
==================================================
LANDING PAGE REQUIREMENTS
Modern SaaS landing page with:

hero section
CTA
animated metrics/cards
feature highlights
“how it works”
trust indicators
FAQ
footer
Design style:

modern startup aesthetic
minimal but premium
dark/light mode support
inspired by Linear, Vercel, Stripe, Ramp
Hero messaging:
Help startups reduce AI infrastructure waste.

Primary CTA:
“Start Free Audit”

==================================================
FORM REQUIREMENTS
Build dynamic multi-section audit form.

Supported AI tools:

Cursor
GitHub Copilot
Claude
ChatGPT
Anthropic API
OpenAI API
Gemini
Windsurf OR v0
For each tool capture:

tool name
selected plan
monthly spend
number of seats
usage frequency
primary use case
Additional fields:

team size

company stage

primary use case:

coding
writing
research
data
mixed
Form Requirements:

validation with Zod
clean UX
step-based flow preferred
progress indicator
mobile optimized
state persistence using Zustand persist/localStorage
form survives refresh
==================================================
AUDIT ENGINE REQUIREMENTS
THIS IS THE MOST IMPORTANT FEATURE.

Do NOT use AI for core audit logic.
Use deterministic rule-based logic.

Build a configurable audit engine with:

pricing tables
recommendation rules
savings calculations
plan optimization
alternative tool recommendations
Logic examples:

Team plan with only 2 users may be overkill
Multiple overlapping AI coding assistants may be redundant
API spend may be optimized with subscriptions
Smaller teams may downgrade plans
Heavy coding users may benefit from Cursor over alternatives
Users paying retail may save via credits
Audit engine must:

generate defensible reasoning
feel financially literate
avoid fake savings
honestly state when setup is already optimized
For each recommendation provide:

current spend
recommended action
monthly savings
annual savings
concise reasoning
==================================================
RESULTS PAGE REQUIREMENTS
Premium dashboard-style UI.

Must include:

total monthly savings
total annual savings
savings hero section
per-tool breakdown
recommendation cards
visual analytics/charts
AI-generated summary
email capture CTA
share button
Conditional logic:
If savings > $500/month:

prominently promote Credex consultation
If savings < $100:

honestly say setup is already optimized
Design must be visually impressive and screenshot-worthy.

==================================================
AI SUMMARY REQUIREMENTS
Use Anthropic API preferred.
OpenAI acceptable.

Generate ~100-word personalized summary.

Summary should:

reference user stack
explain biggest inefficiencies
explain overall optimization opportunities
Handle API failures gracefully:

fallback to templated summary
Create:
PROMPTS.md
with:

exact prompts
reasoning behind prompt design
failed iterations
==================================================
BACKEND REQUIREMENTS
Use Supabase.

Need database tables for:

audits
leads
shareable reports
Store:

audit inputs
audit outputs
generated summaries
share IDs
lead emails
Public shared pages must:

exclude personal details
only show spending data and recommendations
==================================================
EMAIL CAPTURE REQUIREMENTS
After results:

capture email

optional:

company
role
team size
Store in Supabase.

Send transactional email using Resend:

audit confirmation
mention Credex follow-up for large savings
==================================================
ABUSE PROTECTION
Implement at least one:

honeypot
rate limiting
hCaptcha
Document reasoning in architecture/docs.

==================================================
SHAREABLE URL REQUIREMENTS
Each audit gets:

unique public URL
Need:

Open Graph metadata
Twitter preview cards
share-ready visuals
==================================================
TESTING REQUIREMENTS
Create minimum 5 automated tests focused on:

audit engine
savings calculations
recommendation logic
edge cases
Tests must actually run successfully.

Create:
TESTS.md

==================================================
CI/CD REQUIREMENTS
Create:
.github/workflows/ci.yml

Workflow must:

install dependencies
run lint
run tests
run build
==================================================
PERFORMANCE REQUIREMENTS
Target Lighthouse:

Performance ≥ 85
Accessibility ≥ 90
Best Practices ≥ 90
Optimize:

images
hydration
bundle size
loading states
==================================================
REQUIRED DOCUMENTATION FILES
Generate and maintain:

README.md
ARCHITECTURE.md
DEVLOG.md
REFLECTION.md
TESTS.md
PRICING_DATA.md
PROMPTS.md
GTM.md
ECONOMICS.md
USER_INTERVIEWS.md
LANDING_COPY.md
METRICS.md

==================================================
ARCHITECTURE REQUIREMENTS
Create scalable folder structure.

Suggested:

app/
components/
lib/
services/
hooks/
store/
types/
tests/
Create:

reusable UI components
modular audit engine
centralized pricing config
==================================================
CODE QUALITY REQUIREMENTS
Code must be:

clean
readable
typed properly
maintainable
production quality
Use:

meaningful naming
comments where necessary
reusable abstractions
good error handling
Avoid:

massive components
duplicated logic
AI-generated code smell
==================================================
DESIGN REQUIREMENTS
UI should feel:

premium
modern
startup-grade
polished
Use:

gradients subtly
glassmorphism sparingly
excellent spacing
smooth hover states
tasteful animations
Do NOT create:

generic admin template
cluttered interface
excessive colors
==================================================
ENTREPRENEURIAL THINKING
The product should feel like:

a real startup MVP
designed for virality
optimized for lead generation
useful enough for real users
Think carefully about:

onboarding
conversion
trust
user psychology
sharing behavior
==================================================
IMPORTANT ENGINEERING RULES
Never hardcode secrets
Use .env.local
Use server actions/API routes appropriately
Prefer server components where beneficial
Use loading states and skeletons
Handle empty/error states gracefully
Ensure responsive design
Ensure accessibility
==================================================
FINAL EXPECTATION
The final result should feel like:

a real YC startup MVP
Product Hunt ready
polished enough to impress senior engineers and founders
Do not produce placeholder/demo-quality work.
Every screen should feel intentional and production-ready.

Work iteratively.
Explain architectural decisions before major implementation changes.
Prioritize correctness, UX quality, maintainability, and polish.

# Improvement
 the share report button is not working and book credex consultation, fix that 

# follow up with this 
Add Brand Personality
Right now the app is clean but slightly generic.

Add:

small gradients
subtle glow
icons/logos for tools
slightly stronger visual identity

Example:

Cursor logo
Claude logo
OpenAI logo

That will make screenshots MUCH more shareable.

Results Page Needs More “WOW”
Currently:

it feels analytical
but not viral/shareable yet

Add:

“You’re overspending by 18%”
“Potential yearly savings unlocked”
badges like:
High Impact
Duplicate Spend
Underutilized Plan

This creates emotional impact.

Improve the Hero Copy
Current:

“Your Stack Audit Results”

Too generic.

Better:

“You’re Wasting $1,000/Month on AI Tools”
“Your AI Stack Could Cost 18% Less”
“Hidden AI Spend Detected”

This increases screenshot/share value massively.

Add Tool Logos
Your tool selector needs:

OpenAI logo
Claude logo
Gemini logo
Cursor logo

Right now buttons feel slightly empty.

This one change will improve polish A LOT.

Add Recommendation Cards
You need more visible:

before vs after
specific action
reasoning

Example:

OpenAI API

Current Spend: $2400/mo

Recommendation:
Move 40% of usage to ChatGPT Team

Estimated Savings:
$480/mo

Reason:
Your current API usage pattern is closer to subscription-based collaboration workloads.

THIS is the core of the assignment.

Most Important Missing Thing

Your app still needs:

“finance-literate reasoning”

The assignment repeats this MANY times.

You must show:

WHY recommendation exists
WHY cheaper option works
WHY user is overspending

Otherwise it becomes:

“random AI recommendations”

which they specifically warned against.