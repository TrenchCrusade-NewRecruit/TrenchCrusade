---
name: new-recruit-local-validation
description: "Reproduce Trench Crusade issue reports in regular New Recruit, then validate roster-data fixes in the locally imported system with visible legal and illegal checks."
---

# New Recruit Issue and Local Validation

Use this workflow when checking a roster-data issue or validating a change in
New Recruit. Keep the reported behaviour and the proposed fix tied to their
respective game sources.

## Reproduce an issue before changing data

1. Follow the repository's rule-change process: verify the current official
   rule and locate the XML objects that could cause the reported behaviour.
2. Select the regular New Recruit game source, displayed as `Trench Crusade`.
   Confirm that source label in the UI before treating the result as evidence
   of the reported bug. Do not use `Trench Crusade (local)` to decide whether
   the current published system reproduces an issue.
3. Build the smallest roster with the reporter's **exact** unit, variant,
   upgrades, weapon, and equipment selections. Check the visible error badges
   at the list, warband, unit, and option levels; open the relevant validation
   details when available and record the actual message or affected section.
   Distinguish the reported error from unrelated force-level errors. A
   displayed rule or selected item does not establish that the roster is valid.
4. Change only the relevant selection to make the closest legal or illegal
   control case. Record both configurations and their observed validation
   results. If the exact case cannot be reproduced, report it as unverified
   with the attempted selections; do not dismiss or close the issue on an
   approximate test.

## Prepare the local source

When validating a local change:

1. Parse the changed XML and confirm New Recruit is using the exact checkout
   and branch being tested. Select `Trench Crusade (local)` and verify the
   source label in the UI before testing a local change.
2. Check the glasses control at the top of New Recruit. Hot reload must be
   enabled so the local source observes checkout changes. If the control is
   red or disabled, prompt the user to enable it and approve the required
   access; pause local runtime validation until it is enabled. Do not claim a
   local fix passed from a stale or manually assumed catalogue state.
3. If the local source does not exist, open New Recruit's game-management or
   import view and use its local/import control (in some versions this is
   labelled **Select file**). Select `Trench Crusade.gst` from the checkout, or
   grant access to that checkout folder if the application requests a folder.
   The source must include the root `Trench Crusade.gst` and its accompanying
   `.cat` files. Ask the user before interacting with a file picker or granting
   folder access.
4. After changing local data, let hot reload apply the change and validate with
   a fresh local list. Existing lists can retain stale selection state. Do not
   re-import the source or use the file picker just to apply an XML edit; do so
   only if the local source is missing or genuinely broken.

Keep any temporary source setup reversible. Do not overwrite the user's
checkout or leave copied test data in place after validation.

## Create and test rosters

1. Prefix every list created for this workflow with `NR-VALIDATE-`, for example
   `NR-VALIDATE-NAVAL-BASE`. Put the prefix at the beginning so test lists are
   searchable and easy to remove later.
2. Rebuild the exact reported configuration under `Trench Crusade (local)`
   after the change. Test the smallest roster that should be legal and the
   closest roster that should be illegal, preferably changing one relevant
   selection between them. Inspect the error badges and validation details for
   both states; record the selections, message, and result. Verify that a
   formerly invalid case actually loses its error and that an illegal control
   still raises one.
3. Test any relevant leader, variant, equipment, availability, and warband-size
   limits.
4. Check the affected base army as well as the new or changed army. Confirm it
   has not gained an unintended variant, unit, option, or invalid roster path.
5. If the user asks to inspect the result, or if the outcome needs
   interpretation, leave the New Recruit list visible and show the relevant
   list state before continuing.

## Finish cleanly

- Report the regular-source reproduction separately from the local-source
  after-change result, including exact selections, observed errors, and each
  `NR-VALIDATE-` list name.
- Restore any temporary local-source changes and verify the working tree is
  clean apart from the intended implementation change.
- Do not delete the test lists automatically. After validation, explicitly
  offer cleanup, naming the lists: "Validation is complete. I created
  `NR-VALIDATE-...`; would you like me to remove the test list(s)?"
- Delete a list only after the user authorizes that cleanup.
