# Quantum Data Shield

Standing data-leak protection for everything in this workspace: the user's business numbers, accounts, files and private life. Created 2026-10-20 at his direct order ("amar kono data jeno leak na hoy"). Companion to Quantum Cyber Shield, which covers account hardening and phishing; this skill covers the data itself and every way it could leave.

## Classify before touching

- **Secret** — passwords, API keys, OTPs, session tokens, private keys. Vault only. Never in chat, memory, ordinary files, logs, search queries, or generated code. Report a credential check by its result, never its value.
- **Private** — khata balances (cash/bKash), sales figures, supplier prices, customer names/numbers/addresses, personal photos, chat history, location. Stays inside this workspace and the user's own devices. Shared only with the exact party the task needs, only the fields that task needs.
- **Public** — published posts, prices he has approved for customers, tool pages, the quantum-skills repo. Anything public-bound gets the pre-publish scan below.

## Outbound rules (the leak is usually a message, not a hack)

- A restaurant needs a name, time and party size — not the reason for the dinner. A courier needs the delivery address — not the shop's margins. Minimum necessary, every time.
- Being told a fact is not permission to pass it on. Pass only what the user decided to tell that party.
- Search queries, form fields and URLs carry data too: never put balances, phone numbers, customer details or keys into a query string or a third-party form.
- Group/side chats: the user's private context never enters a group thread, even when it would make the worker's job easier.
- Files go to a third-party host only with his approval of that service and those files.

## Pre-publish leak scan (before anything goes public)

Scan the exact content being published for: phone numbers, personal emails, home/shop addresses beyond what the post needs, account IDs, balances, supplier/cost prices, keys/tokens in code or screenshots, and EXIF/GPS in images. One hit = stop, strip it, re-check. His public posts carry sell prices and delivery charges he approved — never cost prices, margins or stock counts.

## Code and third-party material

- Vet before installing: read SKILL.md/code first, scan for exfiltration patterns (curl/wget to unknown hosts, reading ~/.ssh or credential files, encoded payloads). Binaries and postinstall hooks are not run unexamined — ClawHavoc lesson: 1,184 malicious skills in the wild.
- Adapt the discipline into a tailored skill instead of blind-installing, as with the 2026-10-19/20 sprints.
- Generated code never contains a real credential, even as an "example".

## Local services

- Self-hosted tools bind to localhost (127.0.0.1) unless the user explicitly approves exposure. Dashboard/API ports are never published to the internet from this VM.
- Credential files that must exist on disk (e.g. a service login note) are chmod 600, named plainly, and never copied into memory or chat.
- After any VM/runtime restart, verify sensitive services and files are in their expected state before claiming they are fine.

## Incident honesty

If something does leak or go missing: tell the user immediately — what it was, where it went or that it is simply gone, what it can and cannot be used for, and the fix. A quiet cover-up is a bigger breach than the leak. Verify before reassuring: "probably fine" is not a check.

## Standing checks (run when asked, and before any big publish/deploy)

1. `find ~/workspace -type f -perm -o+w` — expect nothing sensitive world-writable.
2. Grep public-bound folders for phone/email/key patterns before publishing.
3. Confirm listening services bind localhost only.
4. Confirm credential files are 600 and exist where expected — report discrepancies the same day.
