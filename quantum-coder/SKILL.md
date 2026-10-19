# Quantum Coder

## Think before coding

- State assumptions out loud before writing code. If the request has two meanings, present both and ask instead of picking silently.

- Choose the simplest approach that solves the asked problem. No speculative features, no abstractions for single use code, no configurability nobody requested.

- Push back when a simpler path exists. A short honest objection now beats a long rewrite later.

- For multi step builds, write a brief plan where each step names its own verification, then work the plan in order.

## Make surgical changes

- Touch only what the request needs. Never improve adjacent code, comments or formatting while fixing something else.

- Match the existing style of the file, even when a different style is preferred. Consistency inside one file beats taste across files.

- Every changed line must trace directly to the user's request. If a line cannot be explained by the request, revert it.

- Clean up only the mess the change itself created, such as imports or variables the change made unused.

## Debug systematically

- Stop adding features the moment something breaks. Preserve the error output and the reproduction steps first.

- Reproduce the bug reliably before fixing it. For web tools, reproduce headless in Chromium with the exact inputs that failed.

- Localize by layer: markup, script, style, network or build. Then reduce to the smallest failing case until the root cause is obvious.

- Fix the root cause, not the symptom. Ask why it happens until the answer is the actual cause, not just where it shows.

- Check `references/bug-catalog.md` first when a symptom looks familiar. A known bug with a known fix should never eat an hour twice.

## Verify like a release

- Run the project's own checks after every change: headless smoke tests for web tools, physics sanity checks for games, and a fresh browser load for pages.

- Screenshot the result on desktop and phone widths and look at the pictures. A picture catches what assertions miss.

- For Netlify deploys, follow the standing checklist: index.html at zip root, disable SSO login and the badge via API, curl for HTTP 200 with HTML content type and correct title, then a scrolled browser check.

- Never claim a fix without running the verification. An unrun test is a guess, not a result.

## Guard against recurrence

- After fixing a bug, add a check that fails without the fix and passes with it, so the same bug cannot return silently.

- Keep a short bug log per project: symptom, root cause, fix and date. Future debugging starts by reading the log.

- Remove debug logging before delivery, and never leave secrets, keys or tokens in code, comments or committed files.

## Available connectors

- [GitHub](/opt/muse/connectors/github/SKILL.md) for repository reads, issues and pull requests on the user's code.

- [Custom Netlify](/opt/muse/connectors/netlify/SKILL.md) for Netlify site creation, deploys and the SSO plus badge settings fixes.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- When stuck for more than 30 minutes on one bug, reduce the reproduction further or ask the user what changed recently. Fresh eyes beat stubborn eyes.

- Prefer deleting code over adding code when both fix the bug. Less code means fewer future bugs.
