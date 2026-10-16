# Ikemen MvD

First game project: a fighting game built on IKEMEN GO using pre-existing community assets
(characters, stages, screenpacks). The owner is new to game dev, so explain steps plainly.

## Engine
- IKEMEN GO v1.0.0 (Windows build), installed 2026-10-15 from github.com/ikemen-engine/Ikemen-GO
- Run: double-click `MvD Test.exe` in this folder (the IKEMEN GO executable, renamed)
- Git repo: copyrighted pack content (chars, stages, music, screenpack art) is gitignored and stays local; only engine, configs and our fixes are committed. When fixing a pack file, add a `.gitignore` exception so the fix is tracked (see beastboy/GoldenGate examples).
- Kept outside OneDrive on purpose (OneDrive sync locks files and breaks loading). Don't move it back under the user folder.

## Layout
- `chars/` one folder per character; register each in `data/select.def` under `[Characters]`
- `stages/` stage `.def` + `.sff`; register in `data/select.def` under `[ExtraStages]`
- `data/` engine config: `select.def` (roster), `system.base.def` (menus/screenpack), `fight.def` (lifebars)
- `_originals/` untouched copies of the stock config files, for diffing or restoring

## Installed content: "DC vs Marvel" WinMUGEN pack (installed 2026-10-15)
- Source: `~/Downloads/DC vs MARVEL mugen(win)-...-001.zip` (zip of 5 zips). Unpacked copy in `C:\Games\_staging\inner` until testing is done.
- 170 chars in `chars/`, ~130 stages in `stages/`, music in `sound/` and `new sound/` (stage .defs reference both by those names).
- Screenpack (menus, lifebars, fonts) in `data/dcvm/`; active via `Motif = data/dcvm/system.def` in `save/config.ini`.
  Revert to stock look: set Motif back to `data/ikemen1/system.def` (original config in `_originals/config.ini`).
- One shared roster: `data/select.def` (the pack's own, 17x14 grid). `data/dcvm/SYSTEM.DEF` points to it via `select = ../select.def`.
  `#leave blank#` entries are intentional empty grid cells.
- Left out on purpose: Winmugen.exe, its plugins/tools, and .exe/.bat/.pl files bundled inside character folders.
- Fixes applied: roster typo `gleengoblin` -> `greengoblin`; `chars/beastboy/beastboy.def` uncommented note on cmd line;
  `stages/GoldenGate.def` music pointed to `new sound/SY's superboy.mp3`.

## Working rules
- Add and test content one piece at a time; community characters are often broken or MUGEN-1.0-only.
- Downloaded assets are untrusted: extract into a fresh staging folder, inspect, then copy in. Never run .exe/.bat files that come with assets.
- Most community assets use ripped commercial sprites: fine for a personal project, never for sale.
