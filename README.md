# MvD Test

A test project for building a fighting game **with AI assistance**: the
fan-made *DC vs Marvel* WinMUGEN game, assembled and converted to run on the
modern open-source [IKEMEN GO](https://github.com/ikemen-engine/Ikemen-GO)
engine, with Claude Code (Anthropic's AI coding agent) doing the setup work.

## What the AI did
- Downloaded IKEMEN GO v1.0.0 and checked it against the official checksums
- Unpacked the DC vs Marvel pack (a zip of zips: about 170 characters and 130 stages, plus music and a screenpack)
- Screened the pack, leaving out bundled executables (the old WinMUGEN program, tools, plugins and scripts)
- Cross-checked the roster against every character folder and stage file, then installed everything
- Moved the pack's screenpack (menus, lifebars, fonts) into its own folder (`data/dcvm/`) so it doesn't overwrite stock files, and made it the active look
- Ran checks that every character and stage file referenced in the configs actually exists, and fixed the bugs found:
  - roster typo that broke Hobgoblin's stage (`gleengoblin` → `greengoblin`)
  - a malformed config line in Beast Boy's `.def` file
  - the Golden Gate stage pointing at a music file that doesn't exist

The git history shows each change. [`CLAUDE.md`](CLAUDE.md) holds the project
notes the AI reads at the start of every session.

## What's in this repository (and what isn't)
**This repository contains the project only: the engine, configuration, roster,
fixes and notes. The game content is not included.** The characters, stages,
music and screenpack art are left out on purpose (see [`.gitignore`](.gitignore)):

- they're ripped from commercial Marvel, DC and Capcom games and soundtracks, so redistributing them isn't ours to do
- they add up to about 3 GB, too big for a GitHub repository

What *is* included: IKEMEN GO itself (MIT license) with its stock, freely
licensed demo content (Kung Fu Man and test stages), the roster
(`data/select.def`), the screenpack's config files (`data/dcvm/*.def`), the
settings file (`save/config.ini`), and the individual files we fixed.

## Getting the assets
The content comes from the **DC vs Marvel** public release for WinMUGEN by
**ss5ace, Buyog2099, PauTo and Magus** (credits from the pack's screenpack).
It circulates on MUGEN community sites such as
[MUGEN Archive](https://mugenarchive.com) (free account required) and
[MUGEN Free For All](https://mugenfreeforall.com). Search for "DC vs Marvel".

The copy used here was a single download, `DC vs MARVEL mugen(win)`,
containing five zips: `chars 1-6`, `chars 7-12`, `chars 13-17`,
`sound & stages` and `other deta`.

To rebuild the full game from a fresh clone:
1. Copy the character folders from all three `chars` zips into `chars/`.
2. From `sound & stages`: copy `stages/` into `stages/` (keep the repository's own `stage1.*` files), `sound/` into `sound/`, and `new sound/` into a `new sound/` folder at the top level.
3. From `other deta/data`: copy everything except `MUGEN.CFG`, `airedit.cfg` and `SELECT.DEF` into `data/dcvm/`, and copy `other deta/font` into `data/dcvm/font/`. Copy `DCvsMarvelcommon1.cns` into `data/` too.
4. Don't overwrite the files this repository already has: they contain the fixes. Skip any `.exe`, `.bat` or `.dll` files from the pack.
5. Run `MvD Test.exe`.

Without the pack, the game still launches using the stock IKEMEN content.
Most characters will show as empty slots on the select screen.

## Running
Windows: double-click **`MvD Test.exe`** (IKEMEN GO renamed). If Windows
SmartScreen warns you, click *More info → Run anyway*.

## Licenses
- IKEMEN GO engine: MIT. Bundled stock screenpack assets: Creative Commons. See `LICENSES.txt`.
- DC vs Marvel content: fan-made, using characters and assets owned by their respective rights holders. Not included here, and not for commercial use.
