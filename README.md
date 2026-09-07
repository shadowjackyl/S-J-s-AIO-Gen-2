# S&J's AIO for Gen 2

**Version 1.0.0** for Gen2Recomp (Gold / Silver / Crystal).

**Made by Shadowjackyl & JadeflowerFoxx** (and a lot of arguing with AI).

Voxel overworld, all 251 catchable Pokémon, Stadium 2 battle models (from **your** ROM), custom glass UI, visible wilds, wild skies, Stadium arenas, and Kanto-in-First-Person style weather.

No Pokémon ROM or extracted game assets are included.

## Install

1. Gen2Recomp (Gold, Silver, or Crystal).
2. **MODS → Import mod .zip** → this zip.
3. Disable conflicting mods: DramaticShapes, Wilds of Kanto, Wild Skies, a second Stadium 2 importer.
4. Optional: **Imported Files** → Pokémon Stadium 2 (USA) `.z64` for 3D Stadium models and arenas. Without a ROM the rest of the AIO still runs (voxel world, wilds, UI, weather). Stadium model/arena rows stay off until a ROM is imported.

---

## What's new in 1.0.3 beta

Everything below is on top of **1.0.2-beta**. Three modules changed
(`All251Catchable`, `StadiumUI`, `RegionMap`); the other 168 are untouched.

**Catch them all, on any cart**

- Every one of the 251 is obtainable on Gold, Silver and Crystal without
  trading. Gaps closed: Ekans/Arbok on Gold, Sandshrew/Sandslash on Silver,
  and Porygon, which was gated behind TRADE EVOS WILD despite not being a
  trade evolution.
- Trade evolutions level up instead of needing a cable — and an item-gated
  one now wants the item in hand, so Slowpoke can still become Slowbro.
  Stone evolutions are untouched.

**Every Pokémon has a nest**

- The Pokédex AREA answers for all 251 on every cart, and each entry is a
  real encounter — except the five in-game legendaries, which name their
  place without being given a wild spawn, so how you get them is unchanged.
  Ho-Oh and Lugia sit on the Tin Tower and in the Whirl Islands; the three
  roaming beasts are tracked live, so AREA names whichever route each one is
  on right now.
- Only grass and water tables count as a nest. Fishing, headbutt, swarms and
  the Bug Contest do not — which is why Caterpie showed nothing on Silver,
  where the contest is its only source.
- Nocturnal and morning-only Pokémon were invisible to the AREA scan, which
  read only a table's day slots.
- The dex screen could not find its own species: the engine keys Pokémon by
  `SPECIES_010` while the screen counts in dex numbers.

**AREA shows where and when**

- Each habitat is tagged **MORN / DAY / NITE**, or **ANYTIME** when there is
  no restriction.
- It opens on the current clock and on the region you are standing in, and
  dims — rather than hides — the places a species is not out at right now.
- The Pokédex and its AREA map now stay skinned during a battle.

**Land Pokémon stay on land** — visible wilds are checked against the
destination cell as they move, so a land Pokémon no longer walks across water
to reach a spot on the far shore.

**Lore-accurate hours and places** — spawn times come from when each species
actually appears in the game's own tables: Ledyba morning, Spinarak and
Hoothoot night, Caterpie morning and day.

## Options & settings

**Every setting is reachable from in-game OPTIONS** — the Mod Manager is a
mirror, not the only way in. OPTIONS carries this mod's own rows plus five
sub-pages — **WILDS**, **ALL 251**, **WEATHER**, **DISPLAY / SPRITES** and the
**CUSTOM UI** studio — and **Pause → STADIUM** holds the 3D battle, model and
arena rows with its own 30-field picker. The same value
stays in sync everywhere. Quick keys this mod registers: `3` steps the VOXEL
render pipeline and `6` steps T-SHIFT; `M` toggles SOUND. Everything else is
reached through its OPTIONS row.

### Wild Pokémon (encounters & all 251)

| Setting | What it does |
| --- | --- |
| **ALL 251** *(OPTIONS → ALL 251)* | Only adds Pokémon this cart can't already get. After a normal encounter roll on a floor that has extras, 35% become an extra — and **which** extra is decided per species: a slot share measured from the games' own tables, so common Pokémon are common and rarities are rare. There is no rate dial to get wrong. |
| **Added legendaries** | One per save: once caught, that legend never rolls again. Their odds start at the floor and lift a little with every badge — barely there at the start, a real possibility by the Elite Four — and they only roll once your party can plausibly face them. |
| **TRADE EVOS WILD** | Let Alakazam, Machamp, Golem, Gengar, Politoed, Slowking, Steelix, Scizor, Kingdra and Porygon2 appear as extras on themed floors. |
| **SHOW WILD MONS** | Draw encounter-table Pokémon as touch-to-battle models in the voxel overworld (OFF = hidden encounters only). |
| **SPAWN AMOUNT** | How many visible grass/cave/water wilds stay near the map (lower first on Android). |
| **CLASSIC STEP ENC** | Keep normal invisible step encounters alongside the visible ones. |
| **WATER MONS** | Swim models / hidden near-water silhouettes / visible silhouettes / classic surf encounters / disabled. |
| **CAVE SPAWNS** | Reachable floor only, mixed with unreachable atmospheric models, classic cave steps, or disabled. |
| **WILD LOOK** | Solid, faded, or silhouette models (town mons/followers/UI unchanged). |
| **IDLE / ROAM / CHASE / HIDDEN MONS** | Idle pauses and looks around; roaming wanders between cells; chasing lets some land/cave wilds pursue you; hidden starts some as dark silhouettes that reveal before battle. |
| **WILD SHINY RATE** | Shiny odds for visible overworld wilds (the battle uses that same shiny), from natural Gen 2 odds to always-on. |
| **TOWN POKÉMON** | Peaceful non-battle Stadium Pokémon in towns. |
| **WILD SKIES / SKY FLOCK** | Ambient flying encounter-table Pokémon above outdoors; flock = how many. |
| **GRASS VIEW** | ABOVE keeps wild models fully visible; IMMERSED sinks them into the grass tufts. |
| **FOLLOWERS** | 0–6 leading party Pokémon trail the player (render-only). |

### Weather & sky

| Setting | What it does |
| --- | --- |
| **WEATHER** | World-space rain in the voxel overworld (OFF / SOMETIMES / ALWAYS). |
| **STORMS** | Thunderheads while raining (OFF / SOMETIMES / ALWAYS). |
| **WX CLOUDS · PUDDLES · UMBRELLAS · LIGHTNING · RAINBOWS** | Toggle each: drifting cloud layers, rain puddles, NPC umbrellas, fork lightning + sky flash, and rainbows. |

### Voxel world & display (OPTIONS)

| Setting | What it does |
| --- | --- |
| **V-GRID** | One-pixel wireframe along every voxel edge. |
| **V-CURVE** | Bend the world down over the horizon, Animal Crossing style (OFF/1/2/3). |
| **WATER** | Reflections: FULL (shore/trees/buildings), SKY (sky + sun/moon only), OFF. |
| **DAYTIME** | SYNC to the wall clock, pin DAY/NIGHT/DUSK/DAWN, or let CYCLE run (ten minutes each). |
| **AA** | Supersample the 3D world to smooth edges (OFF/2X/4X — the priciest row). |
| **HORIZON / HORIZON ART** | 360° panorama around outdoor maps; AUTO picks the biome strip or pin one panorama. |
| **CLASSIC SPRITES** | STADIUM models / GAME BOY cart sprites / GBC COLOR boost. |
| **TOWN MAP** | ON draws this mod's region map on the Pokégear MAP card, the FLY picker and the Pokédex AREA screen. OFF (ENGINE MAP) hands all three back to the game's own town map; nothing else changes. |
| **SOUND** | STEREO (chip channels split) or MONO. |

### Battles & Stadium 2 (ROM for the model/arena rows)

| Setting | What it does |
| --- | --- |
| **3D-BTL** | Fight on the map, shot over the shoulder with parallax drift (OFF = classic screen). |
| **BACK SPRITES** | Keep your own mon on the battle menu from behind instead of on the map. |
| **STADIUM MODELS** | Imported Stadium models in battles, the overworld and Pokédex art. |
| **STADIUM 2 MODEL ANIMS** | Animate those models in battle (OFF holds them on a static pose). Hidden while 3D BATTLE is off. |
| **ANIMATION SOURCE** | ULTIMATE (this mod's native-timed clips) or IMPORTER dispatch. |
| **MODEL SHADER** | Stadium lighting or watercolor-manga. |
| **BATTLE AA** | Supersample the 3D battle scene (2X/4X), capped by the device. |
| **CUT PARTICLES** | Rapidash cut-attack particles. |
| **BATTLE CINEMA** | Body clips before FIGHT/A and trainers hidden until send-out (OFF = GB timing). |
| **STADIUM ARENAS** | ALL BATTLES · TRAINERS / GYM / E4 / RIVAL · GYMS / E4 / RIVAL · GYMS / E4 · CHOICE · OFF. |
| **ARENA CHOICE / FIELD LIST** | The fixed field while ARENAS = CHOICE; the full 30-field picker. |
| **ARENA TIME OF DAY** | Fields follow the wall clock (dusk/night/evening) or stay authored noon. |
| **ARENA SHOT / SHOT TARGET / CAMERA INPUT / CAMERA RESET** | The 21 authentic broadcast shot families + FIELD two-shot; who the follow shots track; free-camera gate; recenter. |
| **MODEL GALLERY / ANIM MAP / IMPORTER CACHE / REBUILD** | Browse all 251 models, and monitor/rebuild the private importer cache. |

### Custom UI & the glass look

| Setting | What it does |
| --- | --- |
| **CUSTOM UI / MENUS** | Master switch for the dark-glass menus (look only). It sits on the OPTIONS list itself rather than inside a glass page, so turning it off never leaves you somewhere you cannot turn it back on. |
| **UI SIZE / TEXT SIZE** | Scale the glass menus and their text (separately). |
| **GLASS TINT / GLASS COLOR / ACCENT** | Panel opacity; panel tint (navy→wine); highlight color (gold/sky/…). |
| **CORNERS / UI FRAME** | Panel rounding and border treatment. |
| **MENU MOTION / BRIGHTNESS / SPEED** | Animated highlight effect and its strength/speed. |
| **HOLIDAY THEME** | Seasonal UI recolor (auto/halloween/winter/valentine/summer). |
| **BATTLE HUD** | CLEAN + GENDER glass cards or CLASSIC GB tiles. |
| **BATTLE / ENEMY / PLAYER HUD SIZE** | Battle card scale — one for both sides, plus a per-side override (AUTO follows BATTLE HUD SIZE). |
| **DIALOG BOX SIZE** | The battle message box size. |

### Experience Share (OPTIONS rows)

| Setting | What it does |
| --- | --- |
| **EXP SHARE** | OFF = vanilla participant/EXP.ALL split; GEN 1 = Exp. All style (fighters share half); GEN 5+ = every alive bench mon gets the half share; BALANCED = GEN 5+ with a level gate; AVERAGE = gate at party average; CUSTOM = per-bench-mon percent rows. |
| **SINGLE EXP SHARE** | Route all shared EXP to the one Pokémon you pick. |
| **LEVEL UP JINGLE** | LEVEL UP fanfare or ITEM pickup chime for share level-ups. |

### Character studio & paint

Pick your character (intro or pause → character grid), then interact with the
bedroom bookshelf/closet to open the paint studio and paint any sprite
pixel-by-pixel, with a live portrait. Character + paint are **bound to the save
slot** and persist across loads; the portrait (trainer card / Oak speech) and
battle back sprite follow your character too. VR headsets get **VR** and
**SMOOTH TURN** rows on OPTIONS.

---

## Known issues (Stadium models, ROM imported)

**Lanturn, Politoed, Wooper, Girafarig, Ursaring, Pupitar** may not match the N64.

## Credits

**Shadowjackyl & JadeflowerFoxx**, with a lot of arguing with AI.

**Big credit to UNDERdecoded (Ceedrack) for making Gen2Recomp(ed)** — this
entire AIO runs on their recompilation engine (https://github.com/UNDERdecoded/Gen2Recomped).

Deftones565 (Stadium 2 Importer) · DramaticShape / UNDERdecodedHD · StadiumBattleFX · pret · Kanto in First Person (horizon art + weather) · ShaneMcGovernIE (SOUND) · **Wilds of Kanto** (katalyste; do not install alongside this AIO) · **Wild Skies** (do not install alongside this AIO) · Gen2Recomp.

See `THIRD_PARTY_NOTICES.md` and `LICENSE`.
