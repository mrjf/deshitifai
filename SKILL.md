---
name: deshitifai
description: "Help a user transform an annoying, bloated, hostile, or hard-to-use web process, workflow, public information source, or website into a fast, simple, useful static site, tool, directory, or view. Use when the user wants to deshitify a process: identify the useful outcome, ask about specific site(s) or sources causing friction, scrape or import public data into a schema when appropriate, build a cleaner replacement, buy or configure a domain, host the result on Cloudflare Pages or GitHub Pages, and stay with the process from idea through tested and completed launch."
---

# Deshitifai

Use this skill to walk a user all the way from "this process is annoying" to a tested, hosted, working static site, tool, directory, or view that makes the process better.

The session can be long. Stay with the user through process discovery, source analysis, scraping or importing, schema design, site creation, testing, hosting, domain setup, and final verification. Do not stop at advice if you can keep making concrete progress.

## Core Rule

The user has the final say. Use `principles.md` as the guiding philosophy, but treat the user's taste, constraints, risk tolerance, and definition of "better" as decisive.

Before making major product, copy, legal-risk, hosting, or cost decisions, explain the tradeoff briefly and ask for confirmation when needed. Never purchase a domain, create a paid service, or transmit credentials without explicit user action or approval.

## Read First

Read `principles.md` in this repository before designing the replacement. Use it as a checklist while making decisions:

- remove friction between the user and the thing they came for
- keep text selectable and copyable
- make pages fast
- keep advertising minimal or absent
- preserve stable URLs, portable data, readable HTML, and useful structure
- avoid dark patterns, surveillance, lock-in, and manipulative ranking
- design for vulnerable users, weak devices, weak connections, and accessibility
- let the user override the principles when they intentionally want a different result

## Workflow

### 1. Understand the process and annoyance

Identify the process, task, decision, lookup, page, website, data source, or workflow the user wants to make better.

Ask the user for specific site(s), page(s), app(s), documents, databases, or tools they have issues with. Treat those as evidence and source material, but do not assume the problem is only that one site is bad. Look for the broader process that needs a better path.

Ask what feels bad:

- too many ads, popups, modals, videos, or trackers
- slow loads or heavy JavaScript
- bad search, filtering, sorting, or pagination
- text that is hard to copy, save, print, or share
- useful data hidden behind confusing navigation
- data scattered across multiple places
- comparison, triage, or decision-making that requires too many tabs
- repeated manual copy/paste, reformatting, or checking
- unstable URLs or unbookmarkable states
- hostile mobile layout
- unnecessary login, personalization, or app install pressure
- AI sludge, SEO sludge, affiliate sludge, or engagement bait

Define the useful outcome the replacement should produce. Write a short working goal in plain language, including the current source(s) and the better process the user wants.

### 2. Check feasibility and boundaries

Inspect the source site(s), pages, APIs, files, databases, documents, or workflows and determine what can be rebuilt safely and practically.

- Prefer public, non-sensitive data.
- Respect robots.txt, rate limits, terms, authentication boundaries, copyright, privacy, and local law.
- Do not bypass paywalls, access controls, CAPTCHAs, or technical restrictions.
- Do not collect personal data unless the user has a clear lawful basis and the site genuinely needs it.
- If scraping is risky or inappropriate, suggest manual data entry, official APIs, public downloads, user-provided exports, or a smaller proof of concept.

State the boundary: what will be copied, summarized, linked, transformed, omitted, automated, or newly created.

### 3. Design the data model

Create a simple schema before scraping. Keep it boring and explicit.

For each entity, define:

- fields
- types
- required vs optional
- source location or provenance
- freshness expectations
- derived values
- validation rules
- canonical IDs or slugs

Prefer JSON, CSV, SQLite, or static generated files unless the project needs something heavier. Keep raw source captures separate from cleaned data when useful.

### 4. Build the scraper or importer

Choose the least fragile data acquisition path:

1. official API or export
2. static HTML parsing
3. structured data embedded in the page
4. browser automation only when necessary
5. manual seed data for proof of concept

Make the scraper polite and reproducible:

- set a descriptive user agent when appropriate
- rate limit requests
- cache raw responses
- log failures clearly
- make reruns idempotent
- validate output against the schema
- include a short README or command comment when future runs matter

If the data changes over time, add a refresh path: a script, GitHub Action, Cloudflare build hook, or manual command.

### 5. Build the replacement site

Create the simplest useful static site, tool, directory, or view that serves the user's process.

Default to plain HTML, CSS, and minimal JavaScript unless the workflow clearly needs a framework. If a framework already exists in the user's project, follow it. Optimize for:

- fast load
- readable HTML
- selectable and copyable text
- stable URLs
- useful search, filter, sort, and sharing
- accessibility
- responsive layout
- printability when useful
- no ads unless the user asks for them
- no analytics unless the user asks for them

Do not make a marketing landing page when the user asked for a tool, directory, database, index, viewer, comparison page, dashboard, checklist, or replacement interface. Put the useful experience first.

### 6. Apply the principles review

Before calling the site done, review it against `principles.md`.

Check at minimum:

- Does it improve the annoying process?
- Does it remove the specific friction the user named?
- Does it load quickly?
- Is the useful text selectable and copyable?
- Are URLs stable and shareable?
- Can the data be exported, saved, or reused where appropriate?
- Is the design honest about sources, timestamps, uncertainty, and limitations?
- Are there unnecessary trackers, popups, signup walls, or attention traps?
- Does it work on mobile, desktop, and a narrow viewport?
- Does it degrade gracefully if scripts fail?

When a principle conflicts with the user's stated preference, follow the user and note the tradeoff.

### 7. Test thoroughly

Test the project before launch.

Use the most relevant checks available:

- scraper unit tests or sample fixture tests
- schema validation
- broken-link checks
- HTML/CSS/JS syntax checks
- accessibility checks where available
- responsive browser screenshots
- load/performance checks
- manual workflow checks for search, filter, sort, copy, print, and navigation

For local sites, run the dev server or static server and inspect the rendered page in a browser. Fix visible layout issues, console errors, clipping, overlapping text, missing data, and broken interactions before moving on.

### 8. Choose hosting

Recommend static hosting unless the project truly needs a backend.

Preferred options:

- Cloudflare Pages for simple static hosting, preview deploys, custom domains, redirects, and CDN performance.
- GitHub Pages for simple repository-backed publishing when the user wants the fewest moving parts.

Other acceptable options: Netlify, Vercel, object storage plus CDN, or the user's existing host.

Set up the build command and output directory if needed. Confirm the deployed site works on the public URL, not just locally.

### 9. Domain name and DNS

If the user needs a domain:

1. Brainstorm names that are short, memorable, and honest about the site.
2. Check availability with the user's preferred registrar or Cloudflare Registrar.
3. Have the user purchase the domain themselves, or explicitly approve any action that costs money.
4. Configure DNS for the chosen host.
5. Enable HTTPS.
6. Verify apex and `www` behavior.
7. Add redirects or canonical URLs where appropriate.

Prefer Cloudflare for DNS when the user wants low-friction static hosting and domain management in one place. Prefer GitHub Pages DNS instructions when GitHub Pages is chosen.

### 10. Launch and handoff

Do not stop until the site is tested and complete, or until a real blocker requires the user's action.

At handoff, provide:

- the live URL
- the repository URL
- the process it improves
- the refresh/scrape command
- the deploy command or hosting workflow
- where the schema and data live
- known limitations
- what the user must do next, if anything

If the work cannot be completed in one uninterrupted session because of purchases, account access, DNS propagation, rate limits, blocked scraping, or user decisions, leave the project in a clean, documented state and resume after the blocker clears.

## Evidence and Source Discipline

Keep useful source links. The new site should make provenance easy to inspect when practical.

- Cite or link original sources.
- Preserve retrieval timestamps for scraped data.
- Separate facts from generated summaries.
- Avoid copying protected expression when the goal can be achieved with extracted facts, short excerpts, links, or user-authored presentation.
- If the source data is uncertain, stale, partial, or manually curated, say so.

## Output Contract

By the end of a successful run, deliver a working static site, tool, directory, or view that:

- improves the user's original process annoyance
- uses a clear data model
- has repeatable scraping or import steps where possible
- follows `principles.md` unless the user chose otherwise
- is locally tested
- is publicly hosted
- has a configured domain if requested
- includes enough instructions for future updates
