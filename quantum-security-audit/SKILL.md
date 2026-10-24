# Quantum Security Audit

## Pick the mode before doing anything

- Guidance mode is the default: a security question, a focused look at one file or flow, or triage of a suspected problem. Use only the relevant parts of this skill. Do not launch a full audit or create report files.
- Full audit mode runs only when Rayhan explicitly asks to audit or pen-test a whole codebase, or asks for a complete security review or a written report. Then work the full pass: map the code, hunt by attack class, validate every candidate, and write the findings up.
- If a request could mean either mode, ask one focused question first instead of guessing.

## Stay inside the defensive boundary

- Audit only code and systems Rayhan owns or is explicitly authorized to test: his own tools and sites, his FreeLLMAPI instance, his custom skills and connectors, his training labs. Anything else is out of scope, full stop.
- Never probe live or shared services, deployed endpoints, or other people's data. All validation happens on source code or in a local sandbox with dummy data.
- Never build payloads, exploit chains, or bypass tooling. The audit describes the smallest effective fix; it does not modify the target source. Fixes are implemented separately, usually through quantum-coder, only when Rayhan asks.
- Running target-controlled code is allowed only sandboxed: no external network, dummy principals and secrets, an empty environment built from an explicit allowlist, and hard limits on time and size. If those controls cannot be enforced, do not execute the code; report the missing control and give a safe validation plan instead.

## Require a boundary and a result

- For every candidate finding, name the lower-trust principal, the accepted input or action, the intended control, the boundary crossed, the affected resource, and the concrete observed result. A candidate missing any of these is not a finding.
- A missing best practice, a checklist deviation, or a generic crash is not a vulnerability. Self-impact and intended same-principal authority are not cross-boundary results.
- Deployment facts that are not in the source (proxy behavior, provider settings, headers, hosting rules) are never assumed present or absent. They become a needs-validation item naming the exact missing fact and the safe check that resolves it.

## Grade only what is confirmed

- Every candidate ends in exactly one state: confirmed, needs validation, or rejected.
- Validation is adversarial and independent: the verifier that confirms or rejects a candidate is never the hunter that found it, and its job is to disprove the candidate on source evidence, not to defend it. A candidate becomes confirmed only when the disproof attempt fails.
- Only confirmed findings receive a severity. Anchor it to the demonstrated result: critical is unauthenticated code execution, full data-store access, or arbitrary account takeover; high is a fully defeated explicit control such as an auth bypass or cross-user data access; medium is a real boundary violation with limited blast radius or uncommon preconditions; low is disclosure of non-secret internals or an effect needing sustained effort for minimal gain. If the concrete damage cannot be stated, the severity is lower than it feels.
- Needs-validation items carry no severity. They state the source-grounded hypothesis, the missing fact, and the safe owner-side or local check.
- For each confirmed finding, recommend the smallest effective source fix: the invariant the code must enforce and the narrowest change that enforces it at the last trusted decision point, plus a regression check. Generic hardening advice is not a fix.

## Hunt by attack class, tuned to his stack

- Work the classes in references/attack-classes.md, selecting only the ones the target actually exposes, and split large targets per subsystem.
- For his single-file HTML tools, start client-side: DOM XSS through innerHTML, unsafe handling of file inputs, secrets or personal data left in localStorage, and metadata or GPS data the tool claims to strip but does not.
- For his Netlify sites, check what ships to the browser: API keys or tokens in client code, admin or debug paths left public, and configuration the deploy exposes.
- For FreeLLMAPI, check the trust edges that matter: provider API keys at rest (file permissions, never in logs or chat), the dashboard's localhost binding, the unified key's handling, and anything that would let a caller reach one tenant's keys or usage from another's.
- For any third-party skill, connector, or script he is considering adopting, the supply-chain class applies first: run the quantum-data-shield vetting before the code is trusted, and treat a failed vet as a confirmed finding against adopting it.

## Report honestly about coverage

- State the profile used (quick or standard) and the scope actually covered. A scoped or quick pass is partial coverage and must say so; never imply one run exhausts a target.
- The report lists confirmed findings with source evidence and fixes, then needs-validation items with their missing facts, then a one-line coverage statement. Rejected candidates are not reported as findings.
- If budget or missing facts stop the pass early, say the audit is incomplete and name the exact gap instead of quietly thinning the evidence.
- Runs are additive: keep the coverage list and findings from each full audit and read them before the next run. Revalidate any prior confirmed finding whose source changed, and re-check prior needs-validation items against the current source. A prior quick or scoped pass contributes only its recorded evidence and gaps; it never implies the rest of the code is fine.

## Available connectors

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md) for reading his own repositories, files and history when the target lives there.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

## Alternatives for better results

- For hacked accounts, Page theft, phishing and OTP traps, use quantum-cyber-shield: it covers the account and social side, this skill covers code.
- For deciding what data may leave the machine and how third-party code gets vetted, use quantum-data-shield; this skill consumes its verdicts.
- To implement a confirmed fix, hand the finding to quantum-coder with the invariant and the regression check attached.
