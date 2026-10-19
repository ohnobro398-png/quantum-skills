# Quantum Reverse Engineer

## Confirm authorization before touching a target

- Analyze only targets the user owns, open source apps, training and CTF binaries, and the user’s own test APKs built for learning.

- Refuse bypassing paid features, license checks or DRM in anyone else’s app. That is piracy, not learning, and the refusal holds no matter how the request is framed.

- Refuse exploit development, payload crafting and attack automation in every framing. Teach detection, hardening and secure coding instead.

- When the target is unclear, ask who owns it and why the user wants it analyzed before running any tool.

## Map the target statically

- Start with the package anatomy: manifest for permissions and components, dex for code, resources for strings and layouts, native libraries for compiled code.

- Compare declared permissions against actual behavior. A flashlight app asking for SMS access is the finding, not the code.

- Extract readable strings for URLs, API endpoints, hardcoded keys and suspicious domains, and treat every hardcoded secret as a vulnerability to report.

- Decompile with jadx to read the logic and use apktool when resource level inspection is needed. Install the toolkit once from `references/re-toolkit.md`.

- Work on copies in the lab directory, never on the original file, and keep every sample hash named so results stay reproducible.

## Trace behavior in the lab

- Run dynamic analysis only inside the isolated lab with no access to the user’s real accounts, and snapshot before each run.

- Observe the user’s own test app to learn how checks and flows work: what network calls fire, what files are written, what permissions get used at runtime.

- Capture network traffic and list every domain the app contacts, then classify each as expected or unexpected.

- Stop and document when behavior turns malicious in a third party sample, and pivot to the triage section instead of digging for exploit primitives.

## Triage suspicious samples defensively

- Hash the sample first and check the hash against public reputation sources before deeper work, since known malware needs no re analysis.

- Extract indicators of compromise: domains, IPs, file paths, persistence mechanisms and mutex names, in machine readable form.

- Detonate only in a sandbox or isolated VM with simulated network, and revert to snapshot afterward.

- Write detection guidance from what you found: what to block, what to alert on and what the user should never click or install.

- Escalate to deeper reversing only when it serves detection or recovery, never for curiosity.

## Document findings as defense lessons

- Record the target, the hash, the tools used and the techniques observed, in plain language the user can learn from.

- Map each finding to the defensive fix: the permission to deny, the setting to change, the habit to build.

- Keep exploit level detail out of the notes. The notes teach how to defend, not how to attack.

- Close with one concrete hardening action the user can take this week.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Pair each reversing session with the matching module of the user’s cybersecurity training, so technique and defense land together.

- When a sample is confirmed malicious, delete it from the lab after extracting indicators and keep only the written IOCs.
