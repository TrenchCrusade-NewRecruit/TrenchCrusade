# Trench Crusade roster-data instructions

## Rule authority

Before changing roster legality, verify the current official rules. The official Rules page and PDFs take priority over existing catalogue behaviour, issues, or community interpretation.

- [Official Rules page](https://www.trenchcrusade.com/rules/)
- [Digital Rulebook 1.0.2 (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Trench-Crusade-Digital-Rulebook.pdf)
- [Warbands of Trench Crusade 1.0.2 (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Warbands-of-Trench-Crusade.pdf)
- [Procession of the Sacred Affliction Warband (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Procession-of-the-Sacred-Affliction-Warband.pdf)
- [Heretic Naval Raiders Warband (PDF)](https://www.trenchcrusade.com/app/uploads/2026/09/Heretic-Naval-Raiders-Warband.pdf)

The PDFs are free to download but must not be committed. Download a dated local copy only when research requires it.

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

## Validation and pull requests

- Keep each rule fix narrowly scoped and independently reviewable.
- Record the official rulebook version and page number in the PR description.
- Parse modified XML and test both the smallest legal case and the case that should fail in New Recruit.
- Do not include locally downloaded PDFs or other third-party rulebook copies.
