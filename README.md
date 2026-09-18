# S&J's AIO for Gen 2

**Version 1.0.61-beta** for Gen2Recomp (Gold / Silver / Crystal).

**Made by Shadowjackyl & JadeflowerFoxx** (and a lot of arguing with AI).

Voxel overworld, all 251 catchable Pokémon, Stadium 2 battle models (from **your** ROM), custom glass UI, visible wilds, wild skies, Stadium arenas, and Kanto-in-First-Person style weather.

No Pokémon ROM or extracted game assets are included.

## Install

1. Gen2Recomp (Gold, Silver, or Crystal).
2. **MODS → Import mod .zip** → this zip.
3. Disable conflicting mods: DramaticShapes, Wilds of Kanto, Wild Skies, a second Stadium 2 importer.
4. Optional: import a Pokémon Stadium 2 (USA) `.z64` for the 3D Stadium models and arenas — **MODS → Manage** this mod, then **Import** beside *Pokémon Stadium 2 (USA) ROM* (the launcher also offers it under Imported Files). The engine checks the file (exactly 67,108,864 bytes) and stores it once for every mod that needs it. Without a ROM the rest of the AIO still runs (voxel world, wilds, UI, weather); the Stadium model/arena rows stay off until the import lands. After a successful import the status row in the STADIUM submenu stops saying NOT IMPORTED, and the 251-model cache builds itself from there.

## Phones (Android & iOS)

The AIO runs on the phone builds of Gen2Recomp — same zip, no separate
download. On-screen touch controls drive the same menus, and every effect
in this mod scales its particle counts down automatically on a phone so
the frame budget survives.

**Importing the Stadium 2 ROM on a phone**

**Tapping IMPORT ROM on the mod's page works now.** It used to race:
Android streams the picked file into place while the game's importer
reads it half-written, deletes it, and fails the size check — so the
ROM vanished and nothing was imported. The mod now shields the pick
while it is still arriving (and rescues the launcher's IMPORT chip
picks the same way): **pick the ROM, wait a few seconds, and the bar
says ROM ADOPTED** — on the mod screen itself or the title screen
after the next boot.

If you would rather not go through the launcher at all:

1. **In game (most reliable):** open this mod's options and use the
   engine's **POKÉMON STADIUM 2 (USA) ROM → CHOOSE** row — that flow
   consumes the file picker's pick correctly on every platform.
2. **By folder:** copy the ROM into the app's save folder — the
   `imports/` inbox inside it (any `.z64` / `.n64` / `.v64` name
   works; the mod validates and adopts it on the next boot). On
   Android that folder lives under `Android/data/<Gen2Recomp
   package>/files/`; connect the phone to a computer or use any file
   manager, drop the ROM in, and launch.

The ROM must be the USA version, exactly 67,108,864 bytes. A wrong
file is rejected with a reason on the title-screen bar and nothing is
overwritten — the ROM is only ever read.

**Performance is a setting now.** Set **PERFORMANCE** to
**AUTO (60 FPS)** (the default) and the mod watches the real frame rate:
if frames drop it steps its effect budget down until they recover, then
quietly steps back up — phones start at the canvas-free SMOOTH tier
automatically. **SHOW FPS** draws a small `58 FPS AUTO SMOOTH` readout
so you can see it working. If you ever want to pin it manually:
**HIGH** (soft glow canvases + full particles), **BALANCED** (same
look, fewer particles), **SMOOTH** (no canvases anywhere), **LITE**
(minimum particles). SPAWN AMOUNT still controls the overworld spawns
separately.

**The outdoor voxel world on a phone.** Interiors were always fast;
outdoors used to crawl, and it was not one bug — it was the outdoor
pass stack running at the panel's full native resolution. Three things
ran every single frame with nothing gating them: the sun's shadow pass
(a whole second render of the world, up to 2048×2048, redrawn whenever
anything so much as shifted), the water's screen-space reflections (a
ray march that reads the depth buffer a couple of dozen times per water
pixel — the single heaviest shader in the mod, and tiled phone GPUs are
the worst hardware in the room for exactly that pattern), and a
full-screen mirror copy the water paid even on its cheaper setting.
Phones now: re-lay the sun at most 20 times a second instead of every
frame (a shadow half a step behind its caster is beneath notice), draw
it at half the resolution at most, run **WATER at SKY** by default (the
same sunset on the lake, none of the march — set it back to **FULL**
any time on OPTIONS ▸ DISPLAY if your phone can take it), and render
the world itself at a deeper AUTO scale (75/65/55% by tier instead of
85/75/60). If you want to claw back more, drop **VOXEL DETAIL** a step
— the row goes all the way down to **40% and 35%** now (the 3D pass's
own resolution; the UI and the touch layer are untouched) — and put
**RENDER DISTANCE** to NEAR. While the readout says **LITE-CUTS** the
town Pokémon and the sky flocks are parked on purpose (the same
models, parked not deleted) — they come back when the frame rate
sustains, or right away if you pin PERFORMANCE to BALANCED or HIGH and
spend the frames on them.

**Reading it off the screen.** Turn **SHOW FPS** on (CUSTOM UI): under
the usual `32 FPS 31ms SMOOTH AUTO` line the readout now draws a second
line — device class, the pass's real pixel size, render scale, water
rung, shadow rung, sun resolution, and the stage timers `T:S… W…` (the
sun pass and the whole world render in milliseconds; W minus S is the
eye passes, where the wild models live) — e.g. `HANDHELD 2340x1080 45%
WATER:SKY SUN:512 SHD:FULL T:S4 W61 LITE-CUTS`. That line is the whole
story of what your phone is doing, and it doubles as the build marker:
an older build draws no second line.

**If shadows misbehave.** The shadow map is the one part of the voxel
world that leans on rarer driver behaviour (a readable depth-stencil
canvas, re-laid while the camera moves), and a phone driver that
handles it badly shows it as flicker. **OPTIONS ▸ DISPLAY ▸ SHADOWS ▸
SIMPLE** trades it away on purpose: the stable drop blobs the fallback
has always drawn — characters only, ground only, no second render of
the world, nothing left that can flicker — and it is faster than FULL
on top. **OFF** is clean sunlight with nothing under anybody.

**When the phone is still losing.** If the frame monitor sees sustained
drops in AUTO, the phone drops one rung deeper on its own — render
scale 45%, sun pass 512, plain water, the overworld herd thinned to a
pair and the town / sky Pokémon parked (encounters and battles are
untouched; the same models, parked not deleted) — and eases back only
when the frames have been healthy for a while, so nothing flickers
between states. Area entry is faster on a phone too: the voxel build
now spends the long frames a slow phone actually has instead of a
desktop-sized slice, so the relief appears in roughly a third of the
time it used to.

---

## What's new in 1.0.5-beta

**Smoother voxel world on PC — and it reaches 60 again.** The frame
budget came back in three cuts. Roaming Pokémon models used to run their
full skeletal animation every frame no matter how far away they were;
now a model animates at full speed near the camera, half rate a few
tiles out, and a slow rate far off — same speed, just time-sampled, and
battles, arenas and the model viewer keep the exact every-frame path.
The camera matrix and per-model draw settings are now shared instead of
rebuilt per model per frame (less garbage for the collector — that was
the recurring stutter). And the auto performance ladder no longer
bounces: a demotion now holds for twenty seconds before the tier can
climb back, and how much of the world loads is decided by your own
PERFORMANCE setting instead of the live frame rate — so a busy moment
can no longer unload and rebuild the surrounding maps (that rebuild
burst was the deep cause of the constant dips, and the far world
popping took the shadows with it). Shadows themselves render exactly as
they did before — frame for frame.

**Water no longer doubles the frame whenever a lake is on screen.** The
WATER row used to start at FULL — the mode that re-renders the entire
world a second time into the lake's reflection, on top of a
per-pixel ray march. On the FPS readout that was the world stage
doubling (W jumping to ~13 ms) the moment any water entered the frame,
sun or no sun. New default is **SKY** — the lake still mirrors the sky,
the sun and the moon — and existing installs are moved to it once,
automatically. Want the full shore-and-trees mirror back? OPTIONS →
WATER, one press; it sticks.

**No FPS cap.** The game used to run vsync-paced, which reads as a
~57-60 FPS ceiling on a PC. **VSYNC** is **OFF (NO FPS CAP)** by
default: frames render as fast as the machine can go (ON puts display
pacing back; VR always paces itself).

**VOXEL DETAIL + RENDER DISTANCE.** The voxel world can render at
85/70/55% of full resolution (AUTO follows the device and the
PERFORMANCE tier — phones render below 100% automatically, at a deeper
75/65/55 ladder), and RENDER DISTANCE decides how much of the world
around the current map stays built (NEAR / NORMAL / FAR, AUTO by
tier).

**The outdoor overworld on phones, fixed.** Interiors ran 60; outdoors
stacked the sun's shadow pass (a second full render of the world, every
frame anything moved, at up to 2048²), the water's ray-marched
reflections (a couple of dozen depth reads per water pixel), and a
full-screen mirror copy the water paid even on its cheap setting — all
at the phone panel's native resolution. Phones now re-lay the sun at
most 20×/second at half the resolution, default **WATER to SKY** (same
sky reflection, no march — FULL is still one tap away), and render at
the deeper AUTO scale above — and a phone still losing the fight drops
one rung further on its own (45% scale, 512 sun, plain water) until the
frames recover. **SHOW FPS** now prints a second diagnostic line (device
class, pixel size, scale, water, sun) so a field report reads straight
off the screen.

**PERFORMANCE + SHOW FPS.** One knob (AUTO / HIGH / BALANCED / SMOOTH /
LITE) scales every effect in the mod; AUTO watches the real frame rate
and holds 60 FPS. SHOW FPS puts the live rate and active tier in the
corner.

**One calm studio edge.** Menu motion is stripped — every panel wears a
single quiet, premium edge (layered light profile, corner nodes, side
rails, 3D bevel), static and cheap. **EDGE BRIGHTNESS** sets its
strength. Glass FX (fire, rain, aurora glass...) are separate and
unchanged.

**Options, organized — and TEXT BACKDROP fixed.** Every list is grouped
by relation, every setting has exactly one in-game home (UI rows in
CUSTOM UI, world rows on OPTIONS ▸ DISPLAY), and the text backdrop
row's wrap can no longer wedge after a draw error.

**Under the hood.** About a tenth of the per-frame throwaway memory
(measured worst case ~1.9 MB → tens of KB), menus that never touch the
collector, and the shared DramaticShapes core synced to the upstream
0.7.40 "Emerald" release. The voxel render itself was put on a diet
too: the palette transform, the atlas lookup and every neighbour's
matrix are now built once per render instead of once per draw site,
and the render target is no longer rebuilt several times a frame --
less garbage for the collector to clean up mid-frame, which reads as
fewer hitches on a phone.

---

## What's new in 1.0.4-beta

A lot of fixes, including the importer which wasn't working.

## What's new in 1.0.4

**The Pokédex now hides everything you have not seen**

- An unseen species discloses no information at all: no name, no number, no
  type, no description, no AREA -- just a `?????` placeholder with ENCOUNTER
  TO REGISTER under it. Entries you have seen (or own) keep their full data.

**A real stage in the dex viewer**

- Seen entries preview their Stadium 2 model on a dedicated stage beside the
  entry text, with the description wrapped in the lane that is left. Narrow
  screens fold the stage to a small corner square; everything always fits.

**Smoother camera**

- The dex camera glides onto the Pokémon instead of jumping as it animates,
  locking to the live pose so a flapping or tail-wagging species never swings
  out of frame.

**Bigger custom palettes**

- GLASS COLOR now offers 30 tints, ACCENT 37 highlights and TEXT COLOR 31
  inks -- the full stadium palette, on the mod-manager page and the CUSTOM UI
  studio alike, keyed to the same stored values so nothing already set shifts.

**UI FX**

- A new UI FX row layers effects over the border of every glass panel --
  menus, dialogue and the battle HUD: RIM FLOW, METEOR, FIREFLY, AURORA VEIL,
  SHIMMER and EMBER RISE, each drawn inside the panel's own border band.

**CUSTOM UI studio on the START menu**

- The full CUSTOM UI studio page opens straight from the pause/START menu
  (CUSTOM UI, beside STADIUM and above OPTION); OPTION and everything under
  it stay exactly where the engine put them.

**Fresh-install robustness**

- The all-251 encounter catalog is now plain Lua 5.1, so it compiles on every
  supported engine build instead of only newer runtimes -- one less thing a
  brand-new install can trip on.
- The Stadium 2 model cache no longer depends on the voxel mode's own tick:
  the importer is driven by an always-on frame hook, so importing the ROM in
  the mod manager starts the 251-model build immediately -- on the title
  screen, in menus, or in play -- instead of sitting on WAITING until some
  other condition happened to tick it.

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
| **SPAWN AMOUNT** | How many visible grass/cave/water wilds stay near the map (also follows the PERFORMANCE tier). |
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
| **WATER** | Reflections: FULL (shore/trees/buildings — re-renders the whole world a second time whenever water is on screen), SKY (sky + sun/moon only — **the default**; on a PC this is most of the look for a fraction of the cost), OFF. |
| **SHADOWS** | FULL is the sun's own pass (shadows climb walls, drape roofs). SIMPLE is the stable, cheap drop blobs (characters only) — the one-tap answer if shadows ever flicker or vanish on your device. OFF draws none. |
| **DAYTIME** | SYNC to the wall clock, pin DAY/NIGHT/DUSK/DAWN, or let CYCLE run (ten minutes each). |
| **VOXEL DETAIL** (in CUSTOM UI) | Resolution the 3D world renders at before scaling up: AUTO (follows PERFORMANCE + device) or 100/85/70/55/40/35%. The deep rungs are for phones — the 3D pass only; the UI is untouched. |
| **RENDER DISTANCE** (in CUSTOM UI) | How much of the world around the current map stays built: NEAR (current map only) / NORMAL / FAR (everything adjacent), AUTO by tier. |
| **VSYNC** (in CUSTOM UI) | OFF (NO FPS CAP, the default) runs uncapped for maximum FPS; ON hands pacing to the display. |
| **AA** | Supersample the 3D world to smooth edges (OFF/2X/4X — only runs at 100% detail). |
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
| **CORNERS** | Panel rounding for the glass and its edge. |
| **EDGE BRIGHTNESS** | How strongly the calm studio edge glows (subtle → nova). |
| **PERFORMANCE** | One knob for the whole effect budget. AUTO holds 60 FPS by watching the frame rate; HIGH / BALANCED / SMOOTH / LITE pin it manually. |
| **SHOW FPS** | A corner readout of the frame rate and the active quality tier. |
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

**Menu freeze-frame.** Opening a menu over the world used to change
nothing about the world pass: the engine pauses the world under a
covering menu (nothing can move), yet the full 3D scene was
re-rendered every frame anyway — the pause screen paid the whole world
price to redraw an identical picture. While a menu covers the world
the last finished frame is now reused; the moment anything about the
view could change — the map, the camera, the hour, the render scale —
it re-renders once. Battles are exempt (their camera and models live
in the same pass), and this changes nothing during normal play: in
gameplay the world renders exactly as it always has.

**Touch camera in arena battles.** The free arena camera (drag to
orbit, zoom, 0 to recentre) was driven by mouse and keyboard only — on
a phone none of that existed. One finger now orbits and two fingers
pinch-zoom, behind the same CAMERA INPUT gate, with the desktop
controls untouched.

**Battle speed.** A new BATTLE SPEED row (NORMAL / 2X / 4X / 10X)
runs battles faster — text, menus and animation — while the music
keeps its normal tempo. It applies to arena battles and ordinary
battles alike, never to the overworld, and a speed you set on the
engine's own SPEED row is always respected.

**Gastly and Haunter in arena battles.** The gas cloud around them is
drawn as billboards anchored to the body — wider than it, and hanging
below its authored float — but both the arena camera's framing and the
floor anchor measured the body alone: close-ups sat too close (the
cloud overflowed the frame and read as "too large") and the cloud sank
through the arena floor. The camera now frames body plus cloud, and
the anchor lifts by the same allowance so the cloud's underside rides
the floor. The KO settle keeps its own placement.

**Battle speed now speeds the models up too.** The engine's
fast-forward scales only its logic step; the arena actors rode an
unscaled per-frame hook, so at 2X/4X/10X the battle text sprinted
while every attack, hit and faint played at normal speed. The actors'
whole presentation clock — clips, deferred impacts, faints, effect
timers — now runs at the battle's live speed. The overworld and its
field Pokémon are untouched, and the arena camera keeps its calm
drift.

**Gastly's gas cloud is the right size now.** His gas quads were
rendering at forty times the scale the other gas Pokémon use — the
same class of size-calibration error this renderer system had once
before for Ponyta's smoke — so the cloud dwarfed him no matter where
the camera sat. Gas cards are now capped at twice the body's own
radius (only a miscalibrated card ever shrinks; every other Pokémon's
effects draw exactly as before), and the camera frames the capped
cloud. Haunter's small allowance from the previous round is withdrawn
— he has no gas cards; his haze is part of his model.

**Gastly's body is half size in arena battles.** His native Stadium
model stands about twice as tall as he reads at beside every other
species on the field, so his arena placement — body, float height,
gas and framing together — is scaled to half. Every other species,
and ordinary battles, are unchanged.

**Levitating Pokémon ride at their proper height in arena battles.**
The hover table every ordinary battle obeys — Gastly, Haunter and
Gengar, Magnemite and Magneton, Koffing and Weezing, Porygon and
Porygon2, Mew, the Hoppip line, Misdreavus, Unown, Celebi — now
applies on the arena field too: a levitator whose model hugs the
ground is lifted to its canonical hover, and the camera pulls back
for high riders exactly as it does for tall ones. Fainting still
settles them onto the field. Sizes stay native Stadium scale
(Gastly's arena body remains at his adjusted half).

**Gastly's half-size treatment is arena-only.** His ordinary-battle
size was right all along: the size ruler shared by ordinary battles,
wilds, town Pokémon and followers is unchanged for every species,
and Gastly's half-size lives solely in the arena placement.

**Fireflies at dusk.** Arena battles now carry the importer's lake
fireflies: at night — and gently through the first evening hours —
sixteen small green-gold motes drift and breathe around the field in
independent rhythms. Their motion is fully deterministic, they draw as
a single reusable mesh, and they allocate nothing after the first
frame, so they cost nothing on mobile.

**The fireflies' lighting half ships alongside them.** The other half
of the importer's firefly work — four very faint point lights that
would let the motes gently touch the ground and the grass near them —
is now in the pack too, resting dormant until a scene shader exists
to carry it. It changes nothing you see today; the pair simply travels
together, complete.

**The engine-core rebase was attempted and withdrawn.** This release
briefly rode the current engine core underneath everything; in the
field it broke battles and put a square around overworld sprites, and
it has been rolled back to the last hair of the last working release.
Everything you see, every setting, every battle behavior and every
model repair is exactly as it was in the previous release — verified
file by file against it before shipping this one.

**The engine under the diorama is the current one, and it is faster.**
The whole voxel core -- terrain building, water, structures, the sun,
the sheets of every sprite -- now rides the up-to-date engine release
instead of the year-old one this pack grew on. What you get from it:
areas build noticeably quicker on a phone (the mesher packs more work
into the frames a handheld actually has), water reflects without paying
for reflections nobody can see at the low rungs, the sun's shadow pass
holds its cadence on struggling devices instead of stuttering the
frame, and chunk meshes are prebaked and cached to disk so a map you
have visited before rises almost instantly. Every setting, screen,
battle behavior and model repair is exactly where you left it -- the
full one-hundred-seventy-check suite passed on the merged engine
before this shipped.

**Pokémon are world-sized in world battles.** A species now stands
the same size everywhere you meet it: roaming beside you, in town, as
a follower, and in a battle staged on the route. Route battles used
to size their models with no upper guard while the world draw had
one, so a pack whose authored height ran small rendered oversized the
moment the battle started — Gastly arriving the size of a tree. Both
draws now share the exact same scale (one ruler, one clamp), and
Gastly's gas cloud — his real bulk — hugs his properly-sized body in
the world the same way it already did in the Stadium arenas you
confirmed looked right. The arenas themselves are untouched.

**Hold B to run — everywhere, including first person.** The pack now
carries running shoes: hold B and your step gets shorter (x2 by
default; x1.5, x3 and x4 on the RUN SPEED row). The step itself is
untouched — collision, encounters, ledges, warps and escorts are
exactly the walk's — you simply cross ground faster. It works on the
overhead view and, for the first time, in the first- and
third-person cameras, capped at four times a walk's pace so a run
never outruns the world's own logic. BOOST BIKE and BOOST SURF rows
let the run apply to the bicycle and surfing if you want it to.
(Vendored from MadeinTaly's Running Shoes, with thanks.)

**Pause menus are smooth again.** The engine-core update's disk cache
wrote every finished chunk to disk the moment it was meshed, and the
mesher deliberately does its heaviest building while a menu covers
the world — so the pause screen ate a burst of file writes. Cache
writes are now queued and drained a couple a frame, and big cache
reads are budgeted the same way, so a menu building the map behind
itself stays as smooth as it was before the engine update.
