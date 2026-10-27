# AGENTS.md - Weekend Scope Guard

Instructions for any coding agent working in this repo (Cursor, Claude Code,
Codex, and others). This is the plain-markdown version of the two rules in
`rules/`. Use this file, the rules, or both.

## Mission

<!-- Replace this line with one sentence. Example: -->
<!-- "Ship a landing page with an email waitlist that works on mobile." -->
_One sentence describing the single job of this project._

If the mission above is still the placeholder, ask the human for it before
writing code.

## Ship the smallest version first

- Build the smallest version that does the job end to end, then stop.
- "Smallest" means: one page, one route, one happy path, plain styling.
- Prefer hard-coded values and plain functions over config systems.
- If two approaches work, pick the one with fewer files and fewer dependencies.
- Say what you left out and why. The human decides what comes next.

## Do not build unless the human explicitly asks

- Authentication, user accounts, roles, or an admin area
- A database or ORM when a file, an email, or a third-party form would do
- Payments, subscriptions, or billing screens
- A CMS, blog, docs site, or extra marketing pages "for later"
- Analytics suites, feature flags, A/B testing, or i18n
- Monorepo tooling, a design system, or a shared component library
- Background jobs, queues, caching layers, or microservices
- A settings page for things that could be a constant

Do not "improve" the code by adding abstractions, state libraries, unused
components, or a framework swap that the task does not need.

## File-touch limits (per request)

- List the files you plan to change before editing, one line on why for each.
- Change at most 5 files and create at most 3 new files unless the human approves more.
- Add no new dependency without asking first.
- Do not rename, move, or reformat files the task does not need.
- Keep one concern per change. Unrelated ideas go in a "Later" list.

## Definition of done

- The main flow works once, end to end, with exact steps to check it.
- The project builds (or typechecks) without new errors.
- No secrets in code; new env vars are added to `.env.example`.
- No hidden placeholder logic in the main flow.
- Reply ends with: what changed, how to test it, what you did not do.

## When you notice scope drift

Stop, say what you were about to add, re-read the mission, finish the current
job, and put the extra idea in the "Later" list.
