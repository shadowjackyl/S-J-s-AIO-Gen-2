# Third-party notices and provenance

## Gen2Recomp / Gen2Recomped engine (UNDERdecoded / Ceedrack)

This mod runs on the **Gen2Recomp(ed)** engine — a recompilation of Pokémon
Gold, Silver, and Crystal — made by **UNDERdecoded (Ceedrack)**. Without that
engine this mod would not exist. Big credit: this AIO only adds to the
foundation they built.

Engine repo: https://github.com/UNDERdecoded/Gen2Recomped

## Pokemon Stadium 2 Importer (Deftones565) -- 1.4.0

`lib/s2v/` contains a vendored copy of
[Deftones565/gen1recomp-mod-stadium2-importer](https://github.com/Deftones565/gen1recomp-mod-stadium2-importer)
(v0.12.0), the Pokemon Stadium 2 extractor/renderer that runs on the
PokePort/Gen1Recomp engine family. It is vendored so this mod's imported
pokemon render through the exact pipeline players see in that mod, and so
its 30 archived Stadium 2 battle fields can stage battles here. 39 of the
43 vendored files are byte-identical to upstream after a mechanical
require-path rewrite; five files are adapted for Gen2Recomp paths and this AIO's arena/UI hooks.

The upstream repository carries no license file at vendoring time; it is
credited here as the author of everything in `lib/s2v/`. No ROM, model
pack, texture, audio, or other game asset from either project is included
-- both caches build locally from the player's own ROM import.

## DramaticShapes base

This bundle contains a modified copy of UNDERdecoded's Gen2Recomped
DramaticShapes voxel renderer. The retained MIT notice is in
`UPSTREAM_DRAMATIC_SHAPES_LICENSE.txt`.

## StadiumBattleFX-derived decoder/renderer components

`lib/stadium2/` contains selected, adapted components from
[anxiousintrovert/StadiumBattleFX](https://github.com/anxiousintrovert/StadiumBattleFX),
under that project’s MIT License, retained verbatim in
`UPSTREAM_STADIUM_BATTLE_FX_LICENSE.txt`.

The included subset is limited to the Stadium 2 ROM normalization/archive
reader, model/texture/animation pack builder, and GPU model renderer needed by
this Gen2Recomped-native bridge. It is re-wired to this bundle’s mod namespace,
private `mod.storage` cache, full National Dex 001–251 count, DramaticShapes
3D-BTL scene, and original procedural effect layer.

No StadiumBattleFX ROM cache, model pack, arena asset, announcer audio, voice
pack, proprietary texture, or other game asset is included.

## CMORTDecoder (SubDrag / N64 Sound Tool)

`lib/stadium2/mort.lua` is an in-mod Lua port of the public-domain
CMORTDecoder reverse-engineered by SubDrag. No Pokémon Stadium audio or ROM
data is included.

## Pokémon Stadium 2 research references

The decoder architecture is informed by publicly documented archive research,
including [pret/pokestadiumgs](https://github.com/pret/pokestadiumgs). This
bundle ships neither its source nor any Pokémon Stadium 2 asset.

## Kanto in First Person horizon panoramas

`assets/horizon/*.png` are the four original painted backdrops from
[mrmushrooms11/kanto-first-person](https://github.com/mrmushrooms11/kanto-first-person)
(KANTO / FUJI / VALLEY / CITY). That project states the panoramas are
original art and ship no ROM data. The cylinder renderer in `lib/Horizon.lua`
is a Gen2Recomped-native reimplementation of the same idea (player-centred
360° skirt, depth writes off) and does not copy the rest of that companion
mod.

## Stereo 5.1 Audio (chip-music SOUND option)

`lib/SurroundAudio.lua` ports the Crystal MONO/STEREO synthesis-worker mix
from [ShaneMcGovernIE/surround-audio](https://github.com/ShaneMcGovernIE/surround-audio)
(1.7.0). That project is MIT-licensed. This bundle does not wrap `love.audio`
or the OpenAL listener; only the pan-aware chip worker and the SOUND option
are integrated.

## Explicitly not bundled

The earlier `randyadr/Gen2-3D-Sprites` Gold/Game2 project is **not** included
or required. This package is a separate Gen2Recomped-native integration and
must not be described as a redistribution of that project. Its visible-wild
layer is original code using Gen2Recomped's public `world.tick` and encounter
surfaces. Its menu layer is a clean Gen2Recomped-native recreation of the
requested dark-glass/battle-selector appearance; no UI source files from that
project are bundled.

## User-generated data boundary

The public ZIP is asset-free. A user may choose a legally owned Pokémon Stadium
2 (USA) ROM through Gen2Recomped’s Imported Files panel; the engine validates
it and this mod builds a private local cache. That ROM and cache are
ROM-derived personal artifacts and should not be redistributed.
