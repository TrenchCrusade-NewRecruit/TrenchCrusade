# Trench Crusade roster-data instructions

## Rule authority

Before changing roster legality, verify the current official rules. The official Rules page and PDFs take priority over existing catalogue behaviour, issues, or community interpretation.

- [Official Rules page](https://www.trenchcrusade.com/rules/)
- [Digital Rulebook 1.0.2 (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Trench-Crusade-Digital-Rulebook.pdf)
- [Warbands of Trench Crusade 1.0.2 (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Warbands-of-Trench-Crusade.pdf)
- [Procession of the Sacred Affliction Warband (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Procession-of-the-Sacred-Affliction-Warband.pdf)
- [Heretic Naval Raiders Warband (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Heretic-Naval-Raiders-Warband.pdf)

The PDFs are free to download but must not be committed. Download a dated local copy only when research requires it.

## Additional warbands

- **The Great Hunger:** [rules PDF](https://cdn.shopify.com/s/files/1/0622/7351/9778/files/The_Great_Hunger_Public_Playtest_1-5.pdf?v=1759784804) (official Creature Caster and Factory Fortress supplement; not included in the core Warbands PDF).

## New Recruit implementation references

Use implementation references to learn how to encode a rule, not to determine what the rule should be:

1. [New Recruit tutorials](https://www.newrecruit.eu/tutorials)
2. [New Recruit Data Author tutorial](https://github.com/DerTanteKethe/custom40k-homebrew-system/wiki/NewRecruit-Data-Author-Tutorial)
3. [BattleScribe data-structure overview](https://github-wiki-see.page/m/BSData/catalogue-development/wiki/Data-structure-overview)
4. [Minimal New Recruit examples](https://github.com/Kemp-J/NRDataExamples/tree/main/SimpleForce)
5. [BSData Warhammer 40,000 10th Edition](https://github.com/BSData/wh40k-10e)
6. [Warhammer: The Old World](https://github.com/vflam/Warhammer-The-Old-World)

When an implementation guide and an official rulebook appear to conflict, follow the rulebook and use the closest supported New Recruit pattern.

## Catalogue editing

The root `.gst` and `.cat` files are BattleScribe-compatible XML:

- `Trench Crusade.gst` holds shared game-system definitions.
- `Equipment.cat`, `Melee Weapons.cat`, and `Ranged Weapons.cat` are reusable library catalogues.
- Faction-named catalogues contain warband entries and legality rules.

Use `rg` to search exact names and stable identifiers before editing.

Preserve existing IDs and imports unless the change genuinely requires a new object. Rules are commonly enforced by `entryLink`, `constraint`, `modifier`, and `condition` elements rather than the displayed item name.

## Data revisions

Revision fields communicate catalogue updates to BattleScribe-compatible clients and New Recruit.

- When a `.cat` file changes, increment that file's root `revision` attribute by exactly one from the target branch.
- When `Trench Crusade.gst` changes, increment its root `revision` attribute by exactly one from the target branch.
- Do not change revisions for documentation-only changes.
- Treat a catalogue's `gameSystemRevision` as compatibility metadata, not a per-edit counter. Change it only when the catalogue must explicitly track a changed game-system definition.
- Existing revision or `gameSystemRevision` inconsistencies are not incidental cleanup. Audit and correct them in a dedicated, validated change.
- Before opening a PR, show the changed root revision attributes in the diff and verify the edited XML parses.

## Rule-change and issue verification

Apply this process before either changing roster data/legality or filing an issue about it.

1. Prove the rule is current.
   - Search the current official rulebook or warband PDF for the exact unit, variant, or rule.
   - Record the source URL, rulebook version, and page number in the change notes or issue body.
   - Treat old issues, catalogue text, community resources, and superseded PDFs as historical context only; they are never rule authority.
   - If the current official source does not contain the claimed rule, do not implement or report the old behaviour as missing. Determine instead whether obsolete catalogue data must be removed.

2. Prove the catalogue behaviour.
   - Locate the exact XML object(s) and the `entryLink`, `constraint`, `modifier`, or `condition` responsible for the result.
   - Reproduce the behaviour in the current New Recruit release whenever practical. Do not infer runtime behaviour solely from displayed descriptions, old reports, or the apparent absence of an XML object.
   - Test both the smallest legal case and the closest case that should fail.

3. Act only with both proofs.
   - For a code change, preserve a concise record of the official source and the before/after validation.
   - For an issue, include the official source, reproduction steps, observed behaviour, expected behaviour, and any old issue links as historical references.
   - Deduplicate by root cause: group reports that stem from the same rule or XML implementation, and search the target repository's existing issues before filing.

## Validation and pull requests

- Keep each rule fix narrowly scoped and independently reviewable.
- Record the official rulebook version and page number in the PR description.
- Parse modified XML and test both the smallest legal case and the case that should fail in New Recruit.
- Do not include locally downloaded PDFs or other third-party rulebook copies.

## Pull request labels

Apply exactly one release-note label to every pull request before opening it:

- `roster` for catalogue or warband roster updates.
- `rules` for changes to roster legality or other rules enforcement.
- `enhancement` for non-rule improvements.
- `bug` or `fix` for corrections to existing behaviour.
- `skip-changelog` only when the pull request should be excluded from release notes.

GitHub groups these labels in generated release notes: `roster`, `rules`, and
`enhancement` appear under "Roster and rules updates"; `bug` and `fix` appear
under "Bug fixes"; unlabeled pull requests appear under "Other changes".
