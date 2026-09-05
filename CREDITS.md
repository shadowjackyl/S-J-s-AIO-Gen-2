# CREDITS

S&J's AIO for Gen 2 combines a lot of people's work. Everyone who made this
possible is credited here and in `THIRD_PARTY_NOTICES.md`. If you use any part
of this project, keep these notices with it.

## The engine this runs on — big credit

**Gen2Recomp(ed)** — a recompilation of Pokémon Gold, Silver & Crystal that
turns the original Game Boy code into a modern, moddable engine.

- **UNDERdecoded (Ceedrack)** — made Gen2Recomped.

Thank you. Repo: https://github.com/UNDERdecoded/Gen2Recomped

## Bundled third-party components

| Component | Where | Author / project | License |
| --- | --- | --- | --- |
| Pokémon Stadium 2 Importer | `lib/s2v/` | Deftones565 — https://github.com/Deftones565/gen1recomp-mod-stadium2-importer | (no license file upstream; credited as author) |
| DramaticShapes voxel renderer (modified) | voxel pipeline | UNDERdecodedHD / DramaticShape — Gen2Recomped DramaticShapes | MIT — see `UPSTREAM_DRAMATIC_SHAPES_LICENSE.txt` |
| StadiumBattleFX decoder/renderer components | `lib/stadium2/` | anxiousintrovert — https://github.com/anxiousintrovert/StadiumBattleFX | MIT — see `UPSTREAM_STADIUM_BATTLE_FX_LICENSE.txt` |
| CMORTDecoder (Lua port) | `lib/stadium2/mort.lua` | SubDrag / N64 Sound Tool | Public domain |
| Stadium 2 archive research | — | pret / pokestadiumgs | Research reference |
| Horizon panorama art | `assets/horizon/*.png` | mrmushrooms11 — Kanto in First Person (original art) | Original art, no ROM data |
| Surround / stereo chip audio | `lib/SurroundAudio.lua` | ShaneMcGovernIE — https://github.com/ShaneMcGovernIE/surround-audio | MIT |

## Influence / design credit (not bundled)

- **Wilds of Kanto** (katalyste) — visible-wild design concept this AIO
  reimplements natively. Do **not** install alongside this AIO.
- **Wild Skies** — ambient-sky design concept, likewise reimplemented and
  conflicting.
- **randyadr/Gen2-3D-Sprites** — an earlier approach that this project is
  deliberately **not** a redistribution of; see THIRD_PARTY_NOTICES.md.

## The AIO itself

Original integration, voxel world glue, wilds, custom UI, arenas, Stadium
bridge, character/paint studio and quality-of-life systems by
**Shadowjackyl & JadeflowerFoxx**.

Pokémon © Nintendo / Game Freak / Creatures Inc. No game assets are included.
