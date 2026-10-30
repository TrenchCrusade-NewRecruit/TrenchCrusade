---
name: audit-gh-issues
description: "Re-audit this repository's open GitHub issues against current rules and New Recruit behaviour, open verified fix PRs, and prepare an evidence-backed report with closure drafts for user approval."
---

# Audit GitHub Issues

Use this skill for a full or partial audit of open issues in the Trench Crusade
roster-data repository. Read `../new-recruit-local-validation/SKILL.md` in full
before testing any roster report or catalogue fix, and follow `AGENTS.md` for
rule authority, XML revisions, validation, PR labels, and Git conventions.

## Establish the current issue set

- Use `gh` to list open issues and relevant open or recently merged PRs. Record
  each issue number and URL. Re-check state before acting: a merged PR may have
  already closed an issue. Read the complete report and linked roster, not just
  its title or an earlier audit summary. A linked roster may contain multiple
  forces; identify the exact force and model with the reported selection. Do
  not assign the defect to the faction named in the issue title by default.
- Group reports by their demonstrated rule or XML root cause, but account for
  every issue separately in the final report. A prior conclusion, closed
  duplicate, or existing PR is context rather than proof.

## Collect evidence before deciding

- For a rules or roster claim, find the exact current official rule and record
  its URL, version, and page. Locate the catalogue object and controlling
  constraint, modifier, condition, or link. If the rule is absent or changed,
  investigate obsolete catalogue data instead of assuming the report is wrong.
- Reproduce the reporter's exact selections in the published `Trench Crusade`
  game in a browser. Inspect validation badges and details; compare the nearest
  legal or illegal control. Follow the referenced validation skill for source
  selection, screenshots, and after-change tests. For a UI or platform report,
  verify the published browser behaviour and which component owns it. When an
  action should navigate, inspect newly opened tabs or windows as well as the
  original page. Use the published browser result to decide whether this
  catalogue repository needs a fix, even when the report came from a mobile
  app. If the reported defect does not reproduce there and has no catalogue
  cause, recommend closing it with the observed browser result and, for an
  app-owned feature, the appropriate New Recruit support path. Do not claim to
  have tested Android or iOS unless that platform was actually tested.
- Isolate the reported rule from unrelated roster errors. Before finding that
  an error does not reproduce or recommending closure, record the exact
  selections and the affected model or option's visible badge state before
  changing selections. If a badge is visible, open it and record its message;
  a roster-level badge alone does not identify the cause. If accessibility or
  DOM text shows no badge, inspect the rendered UI or a screenshot before
  declaring the case valid. An unchecked option or missing error text is not
  proof of validity.
- Treat a shared roster page as evidence of selections, not of current
  validation. Rebuild the relevant force in a fresh `NR-VALIDATE-` list using
  the published source, and verify the badge on the affected model. The source
  selector on a shared page may reflect the viewer's currently selected game.
- Mark a claim **unverified** when the exact configuration, current rule, or
  published browser behaviour cannot be established. Explain the missing
  evidence and keep the issue open; do not turn an approximate test into a
  dismissal.

## Act on the finding

- For a confirmed repository defect, make a narrow fix and open a PR for the
  root cause. Keep distinct causes in separate PRs and link every resolved
  issue with `Fixes #...`. Include the official rule citation and the exact
  before/after and negative-control results. Use the local New Recruit source
  for fix validation as directed by the referenced skill. After switching
  branches or changing the final XML, verify the target data has loaded in a
  fresh list and repeat the decisive legal and illegal cases. The green hot
  reload indicator alone does not prove a branch switch took effect.
- For an already-correct, superseded, duplicate, or out-of-scope report, draft
  a factual public explanation naming the exact roster tested, observed result,
  applicable rule or ownership evidence, and useful next step. Describe a
  proposed fix as tested with updated catalogue data in New Recruit; do not
  suggest it has reached the published game until verified there. Add a
  labelled screenshot when it materially helps a reader check the result.
- Show the user each proposed closing comment and its evidence in the final
  report. Do not post an issue comment or manually close an issue until the
  user approves that specific action. Keep verified bugs open while their PRs
  are pending; follow the referenced skill's closure guidance after merge.

## Deliver the audit report

Give the audit date and a concise row for every issue: finding, official rule
or other authority, exact New Recruit observation, catalogue cause when
relevant, and PR or next action. Link fix PRs. Include the complete proposed
comment text for every issue recommended for closure, clearly separated from
comments already posted. State any validation limits and list the temporary
rosters created during this audit for later cleanup.
