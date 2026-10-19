# Quantum Cyber Shield

## Harden every account first

- Give every account its own long unique password stored in a password manager. Reused passwords turn one leak into every account lost.

- Turn on two factor authentication everywhere it exists: Facebook, Instagram, WhatsApp Business, Gmail and the Meta Business Portfolio. Prefer an authenticator app over SMS codes, since SIM swap attacks steal SMS codes.

- Save backup codes on paper kept offline, not in chat, email or phone notes. Test one code once to confirm they work.

- Turn on login alerts on Facebook and Instagram so every new login sends an immediate notification.

- Review active sessions monthly and log out every device and location the user does not recognize.

- Never enter a password or code from a link in a message, email or SMS. Open the app or type the site address manually instead.

## Lock down the Page and Business Portfolio

- Keep the Page owned by the Business Portfolio, never by a personal profile alone, so losing one login never means losing the Page.

- Keep at least two trusted people as full control admins, so one hacked or lost account cannot lock everyone out. Review the admin list monthly and remove anyone unknown immediately.

- Treat every "copyright violation", "page will be unpublished" or "verify your page" message as a trap. Meta never sends these through Messenger, WhatsApp or SMS, and the links steal logins.

- Verify the business domain in Business settings when the user has one, which blocks impersonator pages from looking official.

- Never add an admin the user has not met and verified through a second channel. One wrong admin hands over the whole business.

## Defeat phishing and social engineering

- Check the address bar before typing any credential. Real Meta logins live on facebook.com and instagram.com only. Close lookalikes such as faceb00k, meta-verification or fb-business-help instantly.

- Never share a one time code with anyone for any reason. No real support agent, buyer or Facebook employee ever needs it. Anyone asking for it is stealing the account.

- Slow down on urgent messages about locked accounts, prize wins or buyer overpayments. Urgency is the attacker's main tool.

- Confirm payment and order details through a second channel before acting when the request is unusual, such as a buyer asking to move the chat off platform or pay extra for fast shipping.

- Keep shop devices updated and lock them with a PIN or biometrics, since an unlocked phone bypasses every online defense.

## Run the protection loop

- Every week, check login alerts and active sessions on Facebook and Instagram, and confirm the Page admin list still shows only known people.

- Act only when something changed: an unknown admin, an unrecognized login, or a disabled alert setting. Most weeks the correct output is "checked, all clear".

- Every month, confirm backup codes still exist offline, recovery email and phone are current, and the second admin still has access.

- Report findings in plain Bangla with exactly what changed and what to do, and stop when everything is clear.

## Respond in the first hour

- Triage by severity: a hacked personal account that owns the Page is critical, a suspicious login alert alone is a watch, and a phishing message received but not clicked is informational.

- For critical cases, start containment within the hour: secure the personal account first, then remove the attacker from Page roles through the Business Portfolio, then change passwords and revoke sessions.

- Follow the step by step playbooks in `references/incident-playbooks.md` for each scenario, and do not skip steps under time pressure.

- After recovery, record what happened, how the attacker got in and what now blocks that path, so the same attack never works twice.

- Never pay anyone who claims they can recover a hacked page for a fee. Recovery goes through official Meta channels only.

## Available connectors

- [Facebook](/opt/hatch/connectors/facebook_cli/CONNECTOR.md) for Page access diagnostics, Page role checks and reading login related Page activity on managed Pages.

- [Instagram](/opt/hatch/connectors/instagram/CONNECTOR.md) for account and profile reads that help verify the account is still under the user's control.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Pair this shield with the user's ongoing cybersecurity training, since each defended attack becomes a lesson that sticks.

- When a new scam pattern appears in Bangladesh, add its exact message wording to the phishing section so future detection is instant.

- If the user ever hires help for the shop, give helpers the lowest Page role that still lets them work, and remove the role the day they leave.
