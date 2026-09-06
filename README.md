# S&J's AIO for Gen 2

**All-in-one overhaul mod for Gen2Recomp(ed)** — Gold / Silver / Crystal.

**Version 1.0.0 beta** · **Made by Shadowjackyl & JadeflowerFoxx** (and a lot of arguing with AI).

> ## Big credit: UNDERdecoded (Ceedrack)
>
> This mod runs on **Gen2Recomp(ed)**, the recompilation of Pokémon Gold,
> Silver & Crystal made by **UNDERdecoded (Ceedrack)**. Without that engine,
> none of this exists. Go get it and say thanks:
> **https://github.com/UNDERdecoded/Gen2Recomped**

---

## What's in the box

- **Voxel 3D overworld** — the world extruded into real geometry, depth-buffered camera, real shadows, tilt-shift, first/third person, day/night and weather (rain, lightning, rainbows, fog).
- **All 251 catchable** (Gold/Silver/Crystal) with a completion catalog.
- **Pokémon Stadium 2 battle models & arenas** — built locally and privately from *your own* Stadium 2 ROM (optional).
- **Visible wild Pokémon** in the overworld (Wilds-of-Kanto style, built in).
- **Wild skies / sky flocks**, **custom dark-glass UI**, battle HUD, followers, Kanto-in-First-Person horizon art, stereo/mono SOUND.
- **Stadium arenas** for gyms / E4 / trainers / all battles.
- Quality-of-life: Exp Share, HM anywhere, horde minigame (Konami code), VR mode hooks, and more.

No Pokémon ROM, ROM patch, Stadium model pack, texture, audio, or other game
asset is included or redistributed. Anything built from your own ROM stays on
your machine.

## Install

1. Install **Gen2Recomp(ed)** (Gold, Silver, or Crystal): <https://github.com/UNDERdecoded/Gen2Recomped>
2. **MODS → Import mod .zip** → `SJ-AIO-Gen2-v1.0.0-beta.zip` (in `releases/`).
3. Disable conflicting mods: **DramaticShapes**, **Wilds of Kanto**, **Wild Skies**, a second **Stadium 2 importer**.
4. Optional: **Imported Files → Pokémon Stadium 2 (USA) `.z64`** for 3D Stadium models and arenas. Without it, the rest of the AIO (voxel world, wilds, UI, weather) still runs.

---

## Options & settings

The mod's settings live in a few places; the **same value shows on more than one
screen and stays in sync** everywhere:

| Where | What it is |
| --- | --- |
| **Mod Manager** (this mod) | Every setting in one place (the full list below). |
| **Pause → STADIUM** | The Stadium 2 screen: models, arenas, cameras, cache status. Always on the start menu. |
| **OPTIONS** | This mod's rows sit right with the engine display modes (VOXEL block), plus **WILDS / WEATHER / DISPLAY** sub-pages and the **CUSTOM UI** studio when the glass UI is on. |
| **Quick keys** | `3 5 6 7 8 9 M` cycle/toggle the common ones with no menu (see bottom). |

**Row tags used below:** (M) Mod Manager · (O) OPTIONS row · (S) Pause → STADIUM ·
(W) OPTIONS → WILDS · (X) OPTIONS → WEATHER · (D) OPTIONS → DISPLAY / SPRITES ·
(U) OPTIONS → CUSTOM UI studio · (K) quick key.

### Wild Pokémon — encounters & the all-251 catalog

| Setting | What it does | Choices (default first) |
| --- | --- | --- |
| **ALL 251 WILDS** (M) | Only adds Pokémon this cart cannot already get. `BALANCED` = 35% of encounter rolls on catalog floors become extras; `100% UNOWNED CYCLE` = every successful roll rotates through still-uncaught extras; `OFF` = no extra wilds. Legends appear once, then stop once owned. | BALANCED / 100% UNOWNED CYCLE / OFF |
| **TRADE EVOS WILD** (M) | Lets Alakazam, Machamp, Golem, Gengar, Politoed, Slowking, Steelix, Scizor, Kingdra and Porygon2 appear as extras on themed floors (off by default — trade evolutions stay level-up only). | OFF / ON |
| **SHOW WILD MONS** (M, W) | Draws encounter-table Pokémon as touch-to-battle models in the voxel overworld instead of hidden step encounters. | ON / OFF |
| **SPAWN AMOUNT** (M, W) | How many visible grass/cave/water wilds are kept near the current map. Lower first on Android. | NORMAL / LOW / HIGH / VERY HIGH |
| **CLASSIC STEP ENC** (M, W) | Keeps normal invisible grass/cave step encounters running alongside the visible ones (hybrid mode). | ON / OFF |
| **WATER MONS** (M, W) | How water encounters appear: swimming models, hidden near-water silhouettes, visible silhouettes, classic surf encounters, or none. | SWIM MODELS / HID SILHOUETTE / SILHOUETTES / CLASSIC ENC / DISABLED |
| **CAVE SPAWNS** (M, W) | Reachable cave floor only, mixed with unreachable atmospheric models, classic cave steps, or disabled. | MIXED / REACHABLE ONLY / CLASSIC ENC / DISABLED |
| **WILD LOOK** (M, W) | Solid models, faded, or silhouettes (town mons, followers and UI unchanged). | SOLID / FADED / SILHOUETTE |
| **IDLE MONS** (M, W) | Visible wilds pause and look around between moves. | ON / OFF |
| **ROAM MONS** (M, W) | Visible wilds wander between valid encounter cells. | ON / OFF |
| **CHASE MONS** (M, W) | A small subset of land/cave wilds pursues the player before the normal close-contact battle. | ON / OFF |
| **HIDDEN MONS** (M, W) | A small subset starts as subtle dark silhouettes and reveals before battle. | OFF / ON |
| **WILD SHINY RATE** (M, W) | Chance a visible overworld wild is shiny (the battle it starts is that same shiny). From Gen-2 natural odds up to always-on (for testing shiny models). | OFF → ALWAYS |
| **TOWN POKÉMON** (M, W) | Peaceful non-battle Stadium Pokémon in towns (walkable cells; never battles). | ON / OFF |
| **WILD SKIES** (M, W) | Ambient flying encounter-table Pokémon above outdoor towns/routes (visual only). | ON / OFF |
| **SKY FLOCK** (M, W) | How many ambient flyers crowd the sky. | HIGH / LOW / NORMAL |
| **GRASS VIEW** (M, W) | `ABOVE` keeps wild models fully visible; `IMMERSED` sinks grass mons into the tuft layer (closer Wilds-style look). | IMMERSED / ABOVE |
| **FOLLOWERS** (M, W) | How many leading party Pokémon trail the player as render-only models (no actor/collision). | 0–6 (0 = off) |

### Weather & sky (outdoor voxel, Kanto-in-First-Person style)

| Setting | What it does | Choices (default first) |
| --- | --- | --- |
| **WEATHER** (M, X) | World-space rain in the voxel overworld (drops, puddles, rainbows sit in the 3D scene). | SOMETIMES / OFF / ALWAYS |
| **STORMS** (M, X) | Thunderheads while it rains (pair WEATHER=ALWAYS for constant storms). | SOMETIMES / OFF / ALWAYS |
| **WX CLOUDS** (M, X) | Drifting cloud layers during weather. | ON / OFF |
| **WX PUDDLES** (M, X) | Rain gathers in puddles on the ground. | ON / OFF |
| **WX UMBRELLAS** (M, X) | NPCs hold umbrellas in the rain. | ON / OFF |
| **WX LIGHTNING** (M, X) | Forked lightning and gentle sky flash during storms. Turn off if flashes are a problem. | ON / OFF |
| **WX RAINBOWS** (M, X) | Rainbows when the sun comes back through the rain. | ON / OFF |

### Voxel world & display (OPTIONS, next to the display modes)

| Setting | What it does | Choices (default first) |
| --- | --- | --- |
| **V-GRID** (O, K5) | One-pixel wireframe along every voxel edge. | OFF / ON |
| **V-CURVE** (O, K7) | Bend the world down over the horizon, Animal Crossing style. | OFF / 1 / 2 / 3 |
| **WATER** (O, K9) | Reflections on water. `FULL` adds screen-space reflections of shoreline/trees/buildings; `SKY` is just sky/sun/moon (most of the look for a fraction of the cost). | FULL / SKY / OFF |
| **DAYTIME** (O) | Pin the outdoor sky to DAY / NIGHT / DUSK / DAWN, let CYCLE run it (ten minutes of sun, ten of moon), or SYNC it to the clock on the wall. | SYNC / DAY / NIGHT / DUSK / DAWN / CYCLE |
| **AA** (O) | Supersample the whole 3D diorama (renders larger, folds back down) to smooth every edge. The most expensive row in the mod — 2X ≈ 1.4× pixels each way, 4X = 2×. | OFF / 2X / 4X |
| **HORIZON** (M, D) | Paints a distant 360° panorama around outdoor maps in the voxel rungs. Off indoors. | ON / OFF |
| **HORIZON ART** (M, D) | `AUTO` picks a biome strip from the map you're in (ocean, city, ruins, fuji, safari…); the named rows pin one panorama everywhere. | AUTO (BY AREA) / KANTO / FUJI / VALLEY / CITY / CANYON / JUNGLE / RUINS / SAFARI / OCEAN / VOLCANO |
| **CLASSIC SPRITES** (M, D) | Which art non-Stadium visuals use: imported models, the plain Game Boy cart sprites, or those sprites with a GBC-style color boost (no third-party rips). Shiny flag still matches. | STADIUM MODELS / GAME BOY / GBC COLOR |
| **SOUND** (M, D) | Crystal's chip-music option: stereo splits channels 1-2 / 3-4 across the speakers; mono sums them. Also toggles with **M**. | STEREO / MONO |

### Battles & Stadium 2 (requires the ROM for the model/arena rows)

| Setting | What it does | Choices (default first) |
| --- | --- | --- |
| **3D-BTL** (O, S, K8) | Fight on the map: the battle draws over the nearest clear ground, shot over the shoulder with a slow parallax drift. Off returns the classic screen. | ON / OFF |
| **BACK SPRITES** (O) | Keep your own Pokémon on the battle menu (seen from behind, original slot) instead of standing it on the map facing the foe. | OFF / ON |
| **STADIUM MODELS** (M, S) | Imported Stadium 2 models in battles, the overworld, and Pokédex art screens. Off preserves the built caches. | ON / OFF |
| **MODEL ANIMS / ANIMATION SOURCE** (M, S) | `ULTIMATE` keeps this mod's native-timed animation layer (move clips, roles, faint lifecycle); `IMPORTER` uses the vendored pipeline's own dispatch. (The **ANIMATIONS** row on the STADIUM screen also allows OFF, which silences both.) | ULTIMATE / IMPORTER (+ OFF on the STADIUM screen) |
| **MODEL SHADER** (M, S) | Authentic Stadium lighting or the inked watercolor-manga treatment. | STADIUM / WATERCOLOR MANGA (CEL) |
| **BATTLE AA** (S, O) | Supersamples the 3D Stadium battle scene while keeping the interface crisp; limited automatically by the device. | OFF / 2X / 4X |
| **CUT PARTICLES** (S) | Restores Rapidash's cut-attack particle effect in battles and model renders. | ON / OFF |
| **BATTLE CINEMA** (M, S) | On: imported body clips play before FIGHT/A and trainers stay hidden until they come out of the ball. Off: GB-synced timing. | ON / OFF |
| **STADIUM ARENAS** (M, S, O) | Which fights stand on imported Stadium 2 fields (fields match the place you're standing). | ALL BATTLES · TRAINERS / GYM / E4 / RIVAL · GYMS / E4 / RIVAL · GYMS / E4 · CHOICE · OFF |
| **ARENA CHOICE** (S) | The fixed field used while STADIUM ARENAS = CHOICE (press A for the full field list, 30 fields). | Free Battle Park (default) etc. |
| **FIELD LIST** (S) | Opens the full field picker page. | action |
| **ARENA TIME OF DAY** (S) | Arena lighting/skies follow the Gen 2 wall clock (dusk, night, indoor evening dark), pin a look, or keep authored noon. | AUTO (CLOCK) / DAY / DUSK / NIGHT / OFF |
| **ARENA SHOT** (S) | Framing while a field owns a battle: AUTO directs at battle beats, FIELD is the plain two-shot, SHOT 01A–21B are the 21 authentic Stadium broadcast shot families with A/B variants. | AUTO / FIELD / 01A–21B |
| **SHOT TARGET** (S) | Which battler the follow shots track (FIELD two-shot ignores it). | PLAYER / ENEMY |
| **CAMERA INPUT** (S) | Free camera on a field-owned battle (drag = orbit, wheel/Q/E = zoom, 0 = recenter); off keeps the chosen shot locked. | ON / OFF |
| **CAMERA RESET** (S) | Reset the arena camera to the authored framing. | action |
| **MODEL GALLERY** (O) | Page all 251 imported models with the live renderer (only when the cache is ready). | action |
| **ANIM MAP / IMPORTER CACHE / REBUILD…** (S, O) | Status readouts and cache rebuild controls for the private Stadium 2 importer. | status / action |

### Custom UI & the glass look

| Setting | What it does | Choices (default first) |
| --- | --- | --- |
| **CUSTOM UI / MENUS** (M) | Master switch for the dark-glass menus (pause, lists, party, dialogue, options, Mod Manager) — look only, never replaces logic/input. | ON / OFF |
| **CUSTOM UI** (O) | Opens the UI studio where every look row lives together, applied live. | action |
| **UI SIZE** (M, U) | Scales the glass menus/lists/party/dialogue geometry and text together (battle HUD has its own row). | 100% / 85% / 115% / 130% |
| **TEXT SIZE** (M, U) | Text size alone, with row/box heights following so nothing clips. | NORMAL / SMALL / LARGE / XL |
| **GLASS TINT** (M, U) | Panel opacity: light lets the world show through; dark maximizes text contrast. | DARK / NORMAL / LIGHT |
| **GLASS COLOR** (M, U) | The tint of every dark-glass panel (menus, dialogue, YES/NO, battle cards, the studio itself). | PLUM / NAVY / SLATE / TEAL / GREEN / CARBON / CRIMSON / AMBER / ICE / INDIGO / SAND / WINE |
| **ACCENT** (M, U) | Highlight color for selected rows, borders, and the selected YES/NO option. | GOLD / WHITE / SKY / ROSE / MINT / ORANGE / VIOLET / CYAN |
| **CORNERS** (M, U) | Panel corner rounding. | SOFT / ROUND / SHARP / PILL / BEVEL |
| **UI FRAME** (M, U) | Border treatment on every glass panel (several preset border skins). | THIN / NONE / THICK / DOUBLE / GOLD LINE / NEON / CHROME / PIXEL / RIBBON / INSET |
| **MENU MOTION** (U) | Animated highlight effect behind selected rows. | GLOW / SHINE / AURORA / SURGE / EMBER / STARDUST / PULSE / OFF |
| **MOTION BRIGHTNESS** (U) | How strong the MENU MOTION effect is. | NORMAL / SUBTLE / VIVID / HIGH / BLAZING / NOVA |
| **MOTION SPEED** (U) | How fast the MENU MOTION effect moves. | NORMAL / SLOW / FAST / VERY FAST / HYPER / LUDICROUS |
| **HOLIDAY THEME** (U) | Seasonal recolor of the glass UI (auto picks from the date). | OFF / AUTO / HALLOWEEN / WINTER / VALENTINE / SUMMER |
| **BATTLE HUD** (M, U) | `CLEAN` = compact glass name/HP cards with ♂/♀ marks, an EXP bar and a caught-ball stamp; `CLASSIC GB` = original Game Boy HUD tiles. | CLEAN + GENDER / CLASSIC GB |
| **BATTLE HUD SIZE** (M, U) | Scales the clean cards about their anchors (foe top-left, yours bottom-right). | 80% / 90% / 100% / 110% / 125% |
| **ENEMY / PLAYER HUD SIZE** (U) | Override the enemy or player card size individually. | AUTO / 80% / 90% / 100% / 110% / 125% |
| **BATTLE DIALOG SIZE** (M, U) | The battle message box's own size (font + padding + box together; stacks with TEXT SIZE). | BIG / CLASSIC / BIGGER / HUGE / MAX |

### Experience Share (OPTIONS rows)

| Setting | What it does |
| --- | --- |
| **EXP SHARE** | OFF uses the vanilla participant/EXP.ALL split. GEN 1 mirrors the Exp. All key item (fighters share half the EXP, whole party rests). GEN 5+ gives every alive bench mon the half share. BALANCED adds a level gate so a bench mon trails the party instead of racing ahead; AVERAGE gates at the party's average level. CUSTOM keeps fighters at full share and lets you set each bench mon's percent (PERCENT rows appear). |
| **SINGLE EXP SHARE** | Route all shared EXP to the one Pokémon you pick. |
| **LEVEL UP JINGLE** | Which sound plays when a share recipient levels: LEVEL UP fanfare or ITEM pickup chime. |

### Character studio & paint (not a settings page — a mode)

- **Character pick** — choose who you play as (heroes, rivals, profs, and every
  trainer class) from the character grid at the intro and on the pause menu.
- **Paint closet** — interact with the bookshelf in your bedroom (or the closet)
  to open the studio: pick a character and paint its sprite pixel-by-pixel per
  side, with a live portrait preview.
- Everything (character **and** paint) is **bound to the save slot** so two
  files never share a look, and it persists across save loads. Your portrait
  (trainer card / Oak speech / front art) and your battle back sprite follow the
  character too.
- VR headsets get their own rows (VR ON/OFF, SMOOTH TURN) under the voxel block on OPTIONS.

---

## Quick keys

| Key | Action |
| --- | --- |
| `3` | Cycle the VOXEL camera ladder (Diorama ↔ first/third person ↔ FULL) |
| `5` | V-GRID (wireframe) on/off |
| `6` | Tilt-shift blur cycle |
| `7` | V-CURVE (world bend) cycle |
| `8` | 3D-BTL (staged map battles) on/off |
| `9` | WATER (reflections) cycle |
| `M` | SOUND stereo/mono |
| Konami code | Horde minigame |

While this mod is enabled the engine's **TILT** (`3` was its key), **GBC FX**
and **BATTLE BG** rows are removed from OPTIONS (they fight the 3D world) and
held at safe values; uninstalling the mod brings them back.

---

## Known issues (Stadium 2 models, ROM imported)

Lanturn, Politoed, Wooper, Girafarig, Ursaring and Pupitar may not match the
N64 exactly.

## Credits

See **[CREDITS.md](CREDITS.md)** and **[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)** for the
full provenance of every bundled component.

Short version:

| Component | Credit |
| --- | --- |
| Gen2Recomp(ed) engine | **UNDERdecoded (Ceedrack)** |
| Stadium 2 Importer | Deftones565 |
| DramaticShapes voxel renderer | UNDERdecodedHD / DramaticShape (MIT) |
| StadiumBattleFX decoder/renderer | anxiousintrovert (MIT) |
| Stadium 2 research | pret/pokestadiumgs |
| CMORTDecoder | SubDrag (public domain) |
| Horizon panoramas + weather idea | mrmushrooms11 · Kanto in First Person |
| Surround/stereo chip audio | ShaneMcGovernIE (MIT) |
| Visible wilds / skies (concepts) | katalyste · Wilds of Kanto & Wild Skies (do **not** install alongside this AIO) |

## Packaging & license

This project's public releases ship as **obfuscated builds** to discourage
casual code copying; the working source tree is kept private. All third-party
code inside is redistributed under its own licenses, retained verbatim in the
release. See `LICENSE` and `THIRD_PARTY_NOTICES.md`.

Pokémon © Nintendo / Game Freak / Creatures Inc. This is a fan project and is
not affiliated with or endorsed by Nintendo or The Pokémon Company.
