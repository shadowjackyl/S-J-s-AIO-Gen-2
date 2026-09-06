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

## What's new in 1.0.2 beta

Everything below is on top of 1.0.1-beta, which rebuilt the Pokégear MAP
card, the FLY picker and the Pokédex AREA panel on the real Gen 2 region map.

**Stadium arenas**

- A trainer battle used to open on the voxel overworld and cut to its Stadium
  field a second later. The field is now decided once, when the battle starts,
  and the fight opens on it.
- The rival is recognised whatever you named him, so RIVAL fights get a field.
- `GYMS / E4` used to behave as ALL BATTLES; it is now the restrictive option
  it claims to be. Link battles count as trainer battles.
- Fields match the place you are standing in. Mt. Silver works at all (the
  maps are `SILVER_CAVE_*`, which nothing matched), Lavender's radio tower is
  no longer a Rocket base, and a gym's speech house is no longer the gym.
- The early rival fights use the field of the place they happen in; RIVAL'S
  FIELD is kept for Victory Road and the Indigo Plateau.
- The Burned Tower, the Ruins of Alph, Dark Cave, Slowpoke Well and Union
  Cave get a dimmed, colder version of the indoor field.
- The Elite Four and the Champion get the announcer in GYMS mode. They never
  did before.

**Battle HUD**

- Every Pokémon showed as female. Gender compares the Attack DV scaled by 16;
  the scale was missing. Breeding and Attract were never affected — only the
  mark this mod draws.
- Shiny Pokémon are now marked with a gold star.
- ENEMY HUD SIZE and PLAYER HUD SIZE did nothing at all; they work now.

**Settings**

- Three of the five WILD SHINY RATE options silently behaved as NATURAL.
- With 3D BATTLE off, the settings that depend on it are hidden rather than
  shown doing nothing.

--- | --- |
| Three abstract blobs standing in for Johto/Kanto | A real region map — coastline, sand shoreline and surf, mountain ranges, forests, Lake of Rage, the full route network, and city blocks that read as towns |
| The **YOU ARE HERE** pin was pinned to 48% / 48% of the card and never moved | The pin sits on the landmark you are actually standing in, resolved from the engine's map id (interiors resolve to their town: `VIOLET_GYM` → Violet City) |
| The FLY list was re-sorted alphabetically while the cursor index stayed the engine's | Engine order in, engine order out — the highlighted row is the destination FLY will actually take, every time |
| No indication which region you were looking at | The page follows the cursor: select a Kanto town and the map turns to Kanto. JOHTO / KANTO tabs, and a per-row region chip in the list |
| Bevel lines and travelling frame glints drawn straight across the map body | The map card is a flat inset with one hairline rim. No nested frame, no motion pass over the map |
| Seam lines between map cells at some UI scales | The landmass is filled as whole horizontal runs at whole-pixel scale, so adjacent cells cannot seam |
| Pokédex **AREA** was a bullet list of map names | AREA draws the region map with a pulsing dot on every habitat, the names beside it, and picks the region where the species actually lives |
| Any screen carrying a `bg` field could be mistaken for a town map | The claim is narrowed to real map states, plus the Pokégear MAP card by name |

Landmark positions come from the published `pokecrystal` landmark table, so
every town, route and cave sits exactly where Gold/Silver/Crystal puts it. The
map itself is drawn procedurally — no Nintendo map art is copied, decoded or
redistributed.

---

## Options & settings

Settings are spread across the **Mod Manager** (this mod), **Pause → STADIUM**,
and **OPTIONS** (this mod's rows sit with the display modes, plus **WILDS /
WEATHER / DISPLAY** sub-pages and the **CUSTOM UI** studio). The same value
stays in sync everywhere. Quick keys: `3` VOXEL camera · `5` V-GRID · `6`
tilt-shift · `7` V-CURVE · `8` 3D-BTL · `9` WATER · `M` SOUND.

### Wild Pokémon (encounters & all 251)

| Setting | What it does |
| --- | --- |
| **ALL 251 WILDS** | Only adds Pokémon this cart can't already get. BALANCED = 35% of rolls on catalog floors become extras; 100% UNOWNED CYCLE rotates through still-uncaught extras; OFF = none. Legends appear once, then stop once owned. |
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
| **SOUND** | STEREO (chip channels split) or MONO. |

### Battles & Stadium 2 (ROM for the model/arena rows)

| Setting | What it does |
| --- | --- |
| **3D-BTL** | Fight on the map, shot over the shoulder with parallax drift (OFF = classic screen). |
| **BACK SPRITES** | Keep your own mon on the battle menu from behind instead of on the map. |
| **STADIUM MODELS** | Imported Stadium models in battles, the overworld and Pokédex art. |
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
| **CUSTOM UI / MENUS** | Master switch for the dark-glass menus (look only). |
| **UI SIZE / TEXT SIZE** | Scale the glass menus and their text (separately). |
| **GLASS TINT / GLASS COLOR / ACCENT** | Panel opacity; panel tint (navy→wine); highlight color (gold/sky/…). |
| **CORNERS / UI FRAME** | Panel rounding and border treatment. |
| **MENU MOTION / BRIGHTNESS / SPEED** | Animated highlight effect and its strength/speed. |
| **HOLIDAY THEME** | Seasonal UI recolor (auto/halloween/winter/valentine/summer). |
| **BATTLE HUD** | CLEAN + GENDER glass cards or CLASSIC GB tiles. |
| **HUD SIZES / DIALOG BOX SIZE** | Battle card scale (global, enemy, player) and the message box size. |

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
