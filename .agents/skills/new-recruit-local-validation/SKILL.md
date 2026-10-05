---
name: new-recruit-local-validation
description: "Validate Trench Crusade roster-data changes in the locally imported New Recruit system, including legal and illegal roster checks, base-warband regressions, visible verification, and cleanup of prefixed test lists."
---

# New Recruit Local Validation

Use this workflow after a roster-data change needs runtime validation. Test the
local checkout in New Recruit, never the remotely hosted catalogue.

## Prepare the local source

1. First follow the repository's rule-change process: verify the current
   official source, locate the XML which implements the behaviour, and parse
   the changed XML.
2. Confirm New Recruit is using the exact checkout and branch being tested.
   Select the local game source, normally displayed as `Trench Crusade (local)`,
   and make sure its top-bar hot-reload control is enabled. With hot reload
   enabled, New Recruit observes changes in the local checkout; do not treat a
   similarly named remote game as evidence for a local change.
3. If the local source does not exist, open New Recruit's game-management or
   import view and use its local/import control (in some versions this is
   labelled **Select file**). Select `Trench Crusade.gst` from the checkout, or
   grant access to that checkout folder if the application requests a folder.
   The source must include the root `Trench Crusade.gst` and its accompanying
   `.cat` files. Ask the user before interacting with a file picker or granting
   folder access.
4. After changing local data, let hot reload apply the change and validate with
   a fresh list. Existing lists can retain stale selection state. Do not
   re-import the source or use the file picker just to apply an XML edit; do so
   only if the local source is missing or genuinely broken.

Keep any temporary source setup reversible. Do not overwrite the user's
checkout or leave copied test data in place after validation.

## Create and test rosters

1. Prefix every list created for this workflow with `NR-VALIDATE-`, for example
   `NR-VALIDATE-NAVAL-BASE`. Put the prefix at the beginning so test lists are
   searchable and easy to remove later.
2. Test the smallest roster that should be legal and the closest roster that
   should be illegal. Record the selections and the observed validation result.
3. Test any relevant leader, variant, equipment, availability, and warband-size
   limits.
4. Check the affected base army as well as the new or changed army. Confirm it
   has not gained an unintended variant, unit, option, or invalid roster path.
5. If the user asks to inspect the result, or if the outcome needs
   interpretation, leave the New Recruit list visible and show the relevant
   list state before continuing.

## Finish cleanly

- Report which local source was used, each `NR-VALIDATE-` list name, and the
  legal and illegal cases checked.
- Restore any temporary local-source changes and verify the working tree is
  clean apart from the intended implementation change.
- Do not delete the test lists automatically. After validation, explicitly
  offer cleanup, naming the lists: "Validation is complete. I created
  `NR-VALIDATE-...`; would you like me to remove the test list(s)?"
- Delete a list only after the user authorizes that cleanup.
