# Weekend Scope Guard

Two small Cursor rules (plus an `AGENTS.md` version) that keep an AI coding
agent on one job. Free, MIT licensed.

Made by Weekend Ship Kit.

## What it is

AI agents rarely fail at small projects because the code is bad. They fail
because the scope grows. You ask for a waitlist form and get auth, a database,
an admin page, and a form library.

This pack gives the agent four plain instructions:

1. **Ship the smallest version first.** One page, one route, one happy path. Then stop.
2. **A do-not-build list.** Auth, databases, payments, CMS, analytics, and other
   "while we're here" features stay out unless you ask for them.
3. **File-touch limits.** At most 5 changed files and 3 new files per request,
   no new dependencies without asking, and a list of planned files before editing.
4. **A definition of done.** It works end to end, it builds, no secrets in code,
   and the reply says what changed, how to test it, and what was left out.

It is not tied to a framework. It works for Next.js, a Discord bot, a script,
or anything else you want to finish in a weekend.

## What's inside

| File | What it does |
|------|--------------|
| `rules/weekend-scope-guard.mdc` | Ship-the-smallest-version rule, do-not-build list, drift checklist |
| `rules/weekend-change-limits.mdc` | File-touch limits and definition of done |
| `AGENTS.md` | The same rules in plain markdown, with a one-line Mission slot |
| `.cursor-plugin/plugin.json` | Plugin metadata (for directories that read it; you can ignore it) |
| `LICENSE` | MIT |

Both rules use `alwaysApply: true`, so Cursor includes them in every Agent chat
in the project.

## Install

### Option A: Cursor project rules

From the root of your project:

```bash
mkdir -p .cursor/rules
cp path/to/weekend-scope-guard/rules/*.mdc .cursor/rules/
```

Then open **Cursor Settings > Rules** (or the Customize panel) and check that
both rules show as "Always Apply". Project rules must end in `.mdc`; a plain
`.md` file in `.cursor/rules` is ignored.

### Option B: AGENTS.md

Copy `AGENTS.md` to the root of your project. Cursor, Claude Code, Codex, and
other agents read it. If your project already has an `AGENTS.md` (some
scaffolds create one), paste these sections into it instead of overwriting
anything you need.

### Then: write your mission

Open `AGENTS.md` and replace the Mission placeholder with one sentence, for example:

> Ship a landing page with an email waitlist that works on mobile.

If you only use the `.mdc` rules, put the mission in a short `AGENTS.md` anyway.
The scope guard tells the agent to read it, and to ask you for one if it is missing.

## Before and after

An illustrative example, not a benchmark. Same prompt in a small Next.js
landing page project:

> Add a waitlist signup form to the landing page.

**Before (no rules)**, a typical agent reply:

- Adds Prisma and a SQLite database "to store signups"
- Adds NextAuth "so you can protect the admin page"
- Creates `/admin` to list signups
- Installs a form library and a validation library for one email field
- 14 files changed, 6 new dependencies
- Ends with "Done! Everything is set up and working."

**After (with Weekend Scope Guard)**, a typical agent reply:

> Planned files:
> - `components/WaitlistForm.tsx` (new): email input, loading and success states
> - `app/api/waitlist/route.ts` (new): validates the email and sends it to your inbox
> - `app/page.tsx`: renders the form under the hero
>
> No new dependencies. I did not add a database or an admin page; signups arrive
> by email. To test: run `npm run dev`, submit an email, check your inbox.
> Later: store signups in a database if email stops being enough.

Three files, one flow, and a summary you can check.

## Customize

- Change the limits. If 5 files is too tight for your project, change the
  number in `weekend-change-limits.mdc`. Keep a number; "small" alone is too vague.
- Edit the do-not-build list. If your job *is* payments, delete that line.
  Add the things your agent keeps adding that you did not ask for.
- Keep the rules short. Cursor recommends focused rules well under 500 lines.

## Want the full packs?

This free pack is the general part. Weekend Ship Kit also sells three small
paid packs that each do one specific job, with stack-specific rules, an
`AGENTS.md`, a `CLAUDE.md`, and copy-paste prompts:

- [Weekend Waitlist](https://4183436663808.gumroad.com/l/fwjzn) ($12): Next.js landing page with an email waitlist
- [Stripe Checkout](https://4183436663808.gumroad.com/l/yqmarg) ($12): Stripe Checkout with a verified webhook
- [Discord Bot](https://4183436663808.gumroad.com/l/epipda) ($12): discord.js slash-command bot
- [All three as a bundle](https://4183436663808.gumroad.com/l/ektnqc) ($29)

You don't need them to use this pack.

## Feedback

Issues and pull requests are welcome. If the agent still drifts with these
rules on, open an issue with the prompt you used and what it added.

## License

MIT. See `LICENSE`.
