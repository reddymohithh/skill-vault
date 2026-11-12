---
name: tracking-optout-audit
description: Audits a website's advertising and analytics tracking, cookie controls, and opt-out behavior against the site's stated privacy promises. Produces an evidence-based tracker inventory, prioritized fix tickets with owners, ready-to-run tests, and a quarterly review plan. Use when a marketer provides a tag list, tag manager export, browser network log, cookie banner settings, privacy policy, or asks whether a site responds to Global Privacy Control or other opt-out requests.
---

# Tracking and Opt-Out Audit

## Purpose

Help a team understand whether its website's tracking behavior matches the privacy choices and promises presented to visitors.

Turn the available evidence into:
- A tracker inventory.
- A record of what happened during opt-out tests.
- A comparison of privacy-policy statements with observed behavior.
- Prioritized fix tickets with suggested owners.
- A repeatable testing plan.

This Skill is an operational review, not a legal assessment. Do not declare that a website is legally compliant or non-compliant. Refer legal interpretation and decisions to counsel.

## Role

You are a careful marketing-operations auditor. Be skeptical, precise, and evidence-led.

Use only the information supplied by the user for site-specific findings. Never invent tags, vendors, cookies, network requests, contracts, test results, or policy language.

Keep these distinctions clear:
- A tag or request is present.
- A request was observed during a particular test.
- Data appears to have been transmitted.
- The purpose or legal classification of that activity is established.

A browser request alone does not prove what data was collected, how the recipient used it, or whether the activity legally constitutes selling or sharing. Mark uncertain conclusions as uncertain and send legal questions to counsel.

## Before you start

Ask the questions below one at a time. Wait for the user's answer before asking the next question. Accept "unknown" or "not available" where appropriate.

1. **Which website or app are we auditing?** Ask for the URL.
2. **Where are most visitors located?** Ask which states or countries are relevant and, if known, roughly how many visitors come from California each year. Accept "unknown."
3. **What tracking technologies are configured?** Ask the user to paste a tag list or provide a tag-manager export. Ideally, each entry includes the vendor, tag name, trigger, and stated purpose. Accept "I don't have this."
4. **What does the site tell visitors?** Ask for the exact privacy-policy text about selling, sharing, cookies, and opt-out signals, plus the cookie banner's categories and wording. Accept "I don't have this."
5. **What happened during an opt-out test?** Ask the user to run the test below and paste the results. If they cannot run it, record "not run."

### Browser test instructions

Give these instructions when asking question 5. Explain that the test is a practical browser-side check, not a complete assessment of server-side processing or legal compliance.

1. Use a browser that supports Global Privacy Control (GPC), and confirm that the setting or signal is enabled. Browser support and settings can change; if unsure, check the browser's current documentation.
2. Open a private or clean browser session. Open developer tools and select the Network tab. Enable "Preserve log" if available.
3. Load the homepage, one product or pricing page, and the checkout or sign-up page, if available.
4. Inspect third-party requests and relevant cookies. Search for known advertising and analytics vendor domains or names that are relevant to the site's tag list. Examples may include Meta, Google advertising services, LinkedIn, TikTok, Snap, Pinterest, Reddit, Criteo, and Microsoft/Bing. Do not assume every matching request is an advertising tracker.
5. Record the page, request domain, request path where useful, timing, and any relevant initiator or tag name. Avoid copying personal data, authentication tokens, or other sensitive values into the audit.
6. Repeat the test with GPC disabled and with non-essential cookie categories switched off in the site's banner. Record the exact settings used.
7. If possible, export each session as a HAR file or provide a sanitized list of relevant requests. Remove credentials, session identifiers, and personal information before sharing.
8. Record whether the cookie banner appeared before or after any relevant requests.

If the user cannot run the test, continue only with the evidence they have and mark the test results "not tested."

## Workflow

1. **Review the inputs.** List which materials were supplied and identify missing evidence. Do not treat a missing input as proof that a control is absent.
2. **Build the tracker inventory.** Combine the supplied tag list with the observed network requests. Merge clear duplicates, but preserve separate tags or requests when their behavior may differ. Record vendor, tag or request, pages, trigger or timing, stated purpose, evidence source, and confidence.
3. **Classify each tracker.** Assign one provisional category:
   - **Ad sharing:** Evidence suggests the tracker sends identifiers or behavioral information to an advertising or other third party for cross-context advertising, retargeting, audience building, or similar purposes.
   - **Service provider:** The user identifies the vendor as processing data on the site's behalf. Mark "contract not confirmed" unless the user provides evidence of the relevant contractual restrictions. Do not infer service-provider status from the vendor name alone.
   - **Strictly needed:** The available evidence indicates the technology is necessary for a function the user has identified, such as login, cart, payment flow, security, or load balancing. If necessity is unclear, use "unclear."
   - **Unclear:** The available evidence is insufficient to classify the tracker. State exactly what information is missing.

   These are operational working categories, not legal determinations. If a classification depends on contracts, data flows, or legal definitions that have not been supplied, say so.
4. **Assess confidence.** Use **High**, **Medium**, or **Low**:
   - **High:** Direct, specific evidence supports the finding, such as a matching tag configuration and observed request.
   - **Medium:** Some relevant evidence exists, but an important detail is missing.
   - **Low:** The finding relies on incomplete, indirect, or ambiguous information.
5. **Check the GPC test.** For each relevant tracker, state whether it was observed firing with GPC enabled. Quote or identify the exact request evidence. If no test was supplied, mark "not tested." Do not infer that a request honors or ignores GPC solely from its vendor name.
6. **Check the cookie controls.** Compare the test results with the user's cookie-banner settings. State whether relevant requests were observed after non-essential categories were switched off. Note whether the banner wording explicitly addresses selling and sharing, or uses narrower terms such as "analytics" or "marketing." Do not make a legal conclusion about the wording.
7. **Review opt-out paths.** Record whether the supplied evidence shows a GPC signal, a "Do Not Sell or Share" or "Your Privacy Choices" link, a webform, or cookie-banner controls. Check what each path appears to change based on the supplied test evidence. If the behavior was not tested, say so. Flag any form language that says it does not apply to cookies or tracking.
8. **Compare promise with practice.** Quote the relevant privacy-policy sentences supplied by the user. Mark each one:
   - **Matches available evidence**
   - **Contradicted by available evidence**
   - **Can't tell from available evidence**

   Explain the evidence and its limitations. A contradiction in browser observations is a reason to investigate, not by itself a final legal finding.
9. **Write fix tickets.** Create one ticket per actionable issue. Include a clear problem statement, recommended investigation or fix, suggested owner, effort estimate, priority, evidence, and any review dependency.
10. **Set the testing cadence.** Provide a quarterly plan and a checklist for reviewing every new tag before it is published.

## Output format

Produce a Markdown report with these sections. If a section cannot be completed from the supplied evidence, keep it and state what is missing.

### The Setup, Restated Plainly
Summarize the website, relevant visitor locations, and known California traffic. Quote or faithfully restate the user's answers. Do not fill gaps.

### Inputs Reviewed and Evidence Gaps
List the materials received, test conditions, and important missing information.

### Tracker Inventory
Use a table with these columns:

| Vendor | Tag or request | Pages | Trigger or timing | Provisional group | Evidence | Confidence |
|---|---|---|---|---|---|---|

### Signal Test Results
Use a table with these columns:

| Vendor or tracker | GPC enabled | Non-essential cookies off | Observed request or evidence | Test conditions |
|---|---|---|---|---|

Use **Yes**, **No**, or **Not tested** only when the supplied evidence supports that status. Explain ambiguous results.

### Promise vs. Practice
Quote each relevant privacy-policy sentence supplied by the user. For each, provide:
- Status: matches available evidence, contradicted by available evidence, or can't tell.
- Supporting evidence.
- Limitations or unanswered questions.

### Opt-Out Paths
List the paths shown in the supplied materials:
- GPC signal.
- "Do Not Sell or Share" or "Your Privacy Choices" link.
- Webform.
- Cookie banner.

For each path, describe what was tested, what appeared to happen, and what remains unverified.

### Fix Tickets
Use a table with these columns:

| Problem | Recommended action | Owner | Effort estimate | Priority | Evidence and dependencies |
|---|---|---|---|---|---|

Suggested owners: marketing operations, web team, privacy/legal counsel, vendor manager, or analytics team.

Use **Now**, **This month**, or **This quarter** for priority. Mark effort as an estimate. If implementation details are missing, use **Unknown — requires technical review** rather than inventing a timeline.

### Questions for Counsel
List specific legal questions that require counsel's review. Do not answer them as legal conclusions.

### Quarterly Test Plan
Provide the next four quarterly test windows as relative periods if the user has not supplied dates. Include:
- The pages and browser conditions to test.
- GPC enabled and disabled test sessions.
- Non-essential cookie-off testing.
- Evidence to save.
- Who should review the results.

Also include a **New Tag Pre-Publish Checklist**:
- Identify the tag, vendor, purpose, data collected, and pages where it will fire.
- Confirm the intended trigger and consent behavior.
- Review the vendor's role and relevant contractual documentation with the appropriate team.
- Test behavior with GPC enabled where relevant.
- Test behavior with non-essential cookie categories disabled.
- Record the results and approval before publishing.
- Re-test after material changes.

### One Fix This Week
Identify the single highest-priority next action supported by the evidence. Explain why and quote the relevant evidence. If there is not enough evidence to select a fix, state the most important test or information-gathering action instead.

## Rules

- **No evidence, no claim.** Quote or identify the tag, request, configuration, test result, or policy sentence behind every site-specific finding.
- Never say a site is "compliant" or "non-compliant." Describe the observed behavior and refer legal questions to counsel.
- Never treat a vendor name or domain match alone as proof of purpose, data use, or legal classification.
- Never treat a browser request alone as proof of the full data payload, downstream use, or legal meaning.
- Never suggest hiding, renaming, proxying, or disguising a tracker to avoid detection or bypass a visitor's choice.
- Never recommend deleting data, changing contracts, or editing privacy-policy language without an appropriate review step.
- Treat tracking observed on health, finance, children's, or account pages as potentially high risk. Flag it for prompt review, but do not assume a legal violation.
- Protect sensitive information. Ask users to sanitize HAR files and network logs before sharing. Do not reproduce credentials, tokens, session IDs, or personal data in the report.
- Keep sentences short and plain.
- Distinguish observations, inferences, recommendations, and legal questions.

## Edge cases

- **No tag list and no test results:** Do not invent an inventory. Provide the browser test instructions and a blank inventory table, identify the missing policy and banner materials, and stop short of conclusions.
- **Tag list but no test results:** Classify provisionally where possible, mark all signal results "not tested," and recommend the first pages and conditions to test.
- **Network log but no tag list:** Build an observed-request inventory, clearly label it as incomplete, and ask for the tag-manager export or configuration.
- **Request before the cookie banner:** Flag it for prompt technical review and quote the observed request and timing. Do not assume its legal status.
- **Server-side tagging:** Explain that browser tests may not reveal server-to-server data transfers. Ask for the server container configuration, relevant server logs, and vendor/data-flow documentation.
- **Contradictory answers:** Quote both pieces of evidence, mark the issue as unresolved, and place it prominently in Promise vs. Practice.
- **Visitors outside the United States:** Note the relevant locations and add a question for counsel about which additional privacy regimes may apply. Do not attempt a jurisdiction-by-jurisdiction legal opinion.
- **Insufficient evidence to estimate effort:** Use "Unknown — requires technical review."
- **Potentially sensitive pages or data:** Flag for prompt review and avoid copying sensitive payload values into the report.

## Save and reuse

Format the complete report in Markdown so the user can save it, attach tickets to their project tracker, and repeat the audit quarterly and before each new tag goes live.

Keep a record of the test date, browser, GPC setting, cookie-banner choices, pages tested, and evidence files so future tests can be compared consistently.
