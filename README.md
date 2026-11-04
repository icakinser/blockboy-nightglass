# Nightglass

*A top-down stealth heist made with [BlockBoy Game Foundry](https://github.com/icakinser/Blockboy-Game-Foundry), a block-based game engine.* This repo holds the playable game, its cartridge, and a step-by-step tutorial that rebuilds it from an empty cartridge.

<p align="center"><img src="screenshots/player.png" width="420" alt="Nightglass running in the BlockBoy player"></p>

**Nightglass** is a top-down stealth heist. Baron Vellum keeps three star seeds he took from the moth orchards. Moth slips into Vellum Glasshouse by night to take them back and leaves by the coal chute. The manor is one open scene of 3 × 3 screens; the seeds can be taken in any order, but the study needs the brass key from the kitchen.

1. **Front garden:** Warden Pell walks the front of the house. The gravel path crunches; the tall grass beside it hides you even while you move.
2. **Grand gallery:** Warden Quill loops the pillars and Warden Mott watches the study door. The boards in front of the door creak unless you sneak. Two reserve wardens wait in the barracks behind a portcullis that opens whenever the alarm rings.
3. **Glasshouse (seed 1):** glass walls stop you but not eyes. A camera sweeps the upper house and calls wardens to where it saw you; ferns hide you.
4. **Kitchen:** Cook Brindle paces in front of the tables; the brass key is behind them.
5. **Study (seed 2):** locked; Steward Ravel stands by the window. The fuse box here cuts the vault camera's power.
6. **Vault (seed 3):** a blinking laser across its door rings the alarm, and so does the camera inside unless the fuses are pulled. Warden Tull walks the antechamber.
7. **Coal yard:** the coal chute out (needs all three seeds), reached through the kitchen.

## Play it

- **In your browser:** download [`index.html`](index.html) and open it. The whole game is in that one file and needs no install or internet connection.
- **On the web:** turn on GitHub Pages for this repo (Settings > Pages > Deploy from branch `main`, folder `/`) and the game plays at `https://icakinser.github.io/blockboy-nightglass/`.
- **In BlockBoy:** open [`nightglass-cartridge.json`](nightglass-cartridge.json) with the editor's **Import** button to see and edit every object, block and rule. The game also ships with BlockBoy itself under **NEW > NIGHTGLASS**.

The controls are listed in [Controls in the finished game](#controls-in-the-finished-game) below.

## Screenshots

| | |
|---|---|
| <img src="screenshots/01-gallery.png" width="400" alt="The gallery: throw a pebble to pull a guard away"><br>The gallery: throw a pebble to pull a guard away | <img src="screenshots/02-glasshouse.png" width="400" alt="The glasshouse and its sweeping camera"><br>The glasshouse and its sweeping camera |
| <img src="screenshots/03-vault.png" width="400" alt="The vault: lasers and the alarm"><br>The vault: lasers and the alarm | <img src="screenshots/04-kitchen.png" width="400" alt="The kitchen and the brass key"><br>The kitchen and the brass key |
| <img src="screenshots/05-study.png" width="400" alt="The study and the steward"><br>The study and the steward | |

## What's in this repo

| File | What it is |
| --- | --- |
| `index.html` | The standalone game, exported from BlockBoy |
| `nightglass-cartridge.json` | The game's cartridge, for loading into the BlockBoy editor |
| `screenshots/` | The pictures in this README |

## Tutorial: build Nightglass step by step

**Nightglass** is a top-down stealth heist. Baron Vellum keeps three star seeds he took from the moth orchards. Moth slips into Vellum Glasshouse by night to take them back and leaves by the coal chute. The manor is one open scene of 3 × 3 screens; the seeds can be taken in any order, but the study needs the brass key from the kitchen.

1. **Front garden:** Warden Pell walks the front of the house. The gravel path crunches; the tall grass beside it hides you even while you move.
2. **Grand gallery:** Warden Quill loops the pillars and Warden Mott watches the study door. The boards in front of the door creak unless you sneak. Two reserve wardens wait in the barracks behind a portcullis that opens whenever the alarm rings.
3. **Glasshouse (seed 1):** glass walls stop you but not eyes. A camera sweeps the upper house and calls wardens to where it saw you; ferns hide you.
4. **Kitchen:** Cook Brindle paces in front of the tables; the brass key is behind them.
5. **Study (seed 2):** locked; Steward Ravel stands by the window. The fuse box here cuts the vault camera's power.
6. **Vault (seed 3):** a blinking laser across its door rings the alarm, and so does the camera inside unless the fuses are pulled. Warden Tull walks the antechamber.
7. **Coal yard:** the coal chute out (needs all three seeds), reached through the kitchen.

This tutorial rebuilds the whole game from an empty cartridge, with every block setting and rule. The six stealth blocks are covered in depth in [the block reference](https://github.com/icakinser/Blockboy-Game-Foundry/blob/main/docs/BLOCK-REFERENCE.md#stealth).

**What you will learn:** a sneaking top-down hero, guards with sight cones, hearing and patrol routes, security cameras, hiding spots (shadow and cover), noisy floors, thrown pebbles as distractions, laser tripwires that blink, an alarm that opens the barracks, a fuse box rule that switches a camera off, keys and locked doors, collect-all-then-exit, floors drawn under everything, and glass that blocks bodies but not eyes.

**Time:** about 3 hours.

---

### Before you start

- **Keep the finished game open for comparison:** in BUILD mode click **NEW** and choose **NIGHTGLASS**. Play it, then save your own work to a separate file.
- **Coordinates.** Every object gives `x, y, w × h`. The manor is a **16 px tile grid**, so most numbers are multiples of 16. Set **SNAP = 16** for walls and floors, 8 for props.
- **Kinds.** Each kind comes with starter blocks; the steps say which to keep. Remove a block with the **×** on its card.
- **Settings** are written as `Setting = value` using the inspector's names; anything not mentioned stays at its default.
- **Rules:** select an object, click **ADVANCED**, then **ADD LOGIC RULE**. Tags are typed in the same ADVANCED section (**TAGS**).
- **Draw order is object order.** Objects placed first are drawn first (underneath). That is why the floors are Part 2.

#### Controls in the finished game

| Key                            | Does                             |
| ------------------------------ | -------------------------------- |
| Arrows / WASD                  | Walk (heard by wardens)          |
| Hold X (B)                     | Sneak: slow and silent           |
| C                              | Throw a pebble ahead (8 of them) |
| Walk into a warden from behind | Knock him out for 14 seconds     |

---

### Part 1: Set up the scene

1. **NEW > EMPTY GAME.** Delete the ground strip.
2. Rename the scene **VELLUM GLASSHOUSE**, **W = 960**, **H = 720** (60 × 45 tiles).
3. **CAMERA = Follow player.**
4. Palette: **COPY** a built-in palette, name it **Nightglass**: Ink `#0e0c1c`, Dark `#2c2a48`, Light `#8f8cc0`, Paper `#ece8f8`. **USE FOR THIS LEVEL**.
5. **INTRO = TAKE BACK 3 STAR SEEDS, UNSEEN.**

The rooms (one screen each):

|                  | x 0 to 320 | x 320 to 640         | x 640 to 960     |
| ---------------- | ---------- | -------------------- | ---------------- |
| **y 0 to 240**   | Vault      | Study (locked)       | Upper glasshouse |
| **y 240 to 480** | Kitchen    | Grand gallery        | Lower glasshouse |
| **y 480 to 720** | Coal yard  | Front garden (start) | East lawn        |

---

### Part 2: Floors first

Nine floor pieces, one per room, each a **Spikes** object of exactly one screen with its **Hazard block removed** (no blocks at all, so it is just a picture you walk over). Place them before anything else so they draw underneath.

| Name                   | x   | y   | Texture       |
| ---------------------- | --- | --- | ------------- |
| Vault floor            | 0   | 0   | checker tiles |
| Study floor            | 320 | 0   | floorboards   |
| Upper glasshouse floor | 640 | 0   | checker tiles |
| Kitchen floor          | 0   | 240 | checker tiles |
| Gallery floor          | 320 | 240 | floorboards   |
| Lower glasshouse floor | 640 | 240 | checker tiles |
| Coal yard floor        | 0   | 480 | flagstones    |
| Front garden lawn      | 320 | 480 | lawn          |
| East lawn              | 640 | 480 | lawn          |

All are `320 × 240`. For each texture draw one 16 × 16 tile in **SPRITE** and set **ON BIG OBJECTS = Repeat as tiles**. Save one floor as an entity per texture to reuse it.

---

### Part 3: Moth and the world settings

1. Select the hero, rename **Moth**, `466, 672, 12 × 16`.
2. Remove **Gravity, Run, Jump, Double jump, Dash, Stomp attack, Dash attack**.
3. Add **Top-down move** at the top: `Top speed = 82`, `Acceleration × = 2`.
4. Add **Footsteps**: `Footsteps heard within = 56`, `Sneak speed × = 0.45`, `Sneak button = B (X key)`.
5. Add **Key input**: `Key = C key`, `Trigger mode = On press`, `Cooldown = 0.4`. Under **RUN THESE BLOCKS** add **Noise maker**: `Heard within = 112`, `Makes noise = When run (Key input, Timer, rule)`, `Thrown ahead = 96`, `Uses = 8`. The HUD shows `C:PEBBLE` and the count.
6. **Damage + respawn**: `Max hearts = 3`, `Invulnerable after hit = 1.5`, `Knockback = 0`. Keep **Heart collector, Core collector, Exit reader, Checkpoint reader**.
7. **TAGS = thief** (ADVANCED). The fuse box rule checks for it.
8. Sprite: `idle`, `move` (2 frames, 0.14 s) and `sneak` (a crouched frame). Footsteps plays `sneak` while the button is held.

**World settings:** **Checkpoint** `16, 496, 8 × 8`, remove Checkpoint flag, add **Environment settings** with `Pixel sprites = Flip to face movement`, and a rule `WHEN onStart · TARGET self · DO Show / hide (hide)`.

---

### Part 4: Noisy floors and hiding spots

These go **before the walls and the people**, so they draw under them. All are **Spikes** with the Hazard block removed.

#### Noisy floors (Noise maker)

| Name          | x, y, w × h        | Heard within | Makes noise                     |
| ------------- | ------------------ | ------------ | ------------------------------- |
| Gravel path   | 448, 496, 80 × 128 | 144          | When walked on, even sneaking   |
| Creaky boards | 416, 256, 128 × 32 | 96           | When walked on, unless sneaking |
| Study boards  | 400, 144, 160 × 32 | 96           | When walked on, unless sneaking |

`Thrown ahead = 0`, `Uses = 0` for all three. Gravel always crunches; boards are quiet if you sneak. Draw gravel and floorboard tiles, Repeat as tiles.

#### Hiding spots (Hiding spot)

**Shadows** hide Moth only while standing still (`Hides = Shadow: only while standing still`). **Cover** hides even while moving (`Hides = Cover: even while moving`). Leave `Moving in shadow, seen within = 28` for all.

| Name               | x, y, w × h        | Hides  |
| ------------------ | ------------------ | ------ |
| Tall grass W       | 336, 560, 112 × 32 | Cover  |
| Tall grass E       | 528, 560, 112 × 32 | Cover  |
| Lawn grass         | 720, 512, 32 × 176 | Cover  |
| Gallery shadow     | 336, 416, 48 × 48  | Shadow |
| Barracks shadow    | 528, 320, 32 × 32  | Shadow |
| Pantry shadow      | 16, 384, 48 × 80   | Shadow |
| Yard shadow        | 16, 496, 64 × 64   | Shadow |
| Antechamber shadow | 256, 160, 48 × 64  | Shadow |
| Study curtain      | 336, 160, 32 × 64  | Cover  |
| Window curtain     | 592, 144, 32 × 80  | Cover  |
| Fern A             | 672, 64, 32 × 32   | Cover  |
| Fern B             | 736, 160, 32 × 32  | Cover  |
| Fern C             | 848, 176, 32 × 32  | Cover  |
| Fern D             | 688, 288, 32 × 32  | Cover  |
| Fern E             | 880, 304, 32 × 32  | Cover  |
| Fern F             | 768, 384, 32 × 32  | Cover  |

Sprites: a dark hatch for shadows, tall grass and velvet curtains (Repeat as tiles), and a potted fern (one 32 × 32 picture, stretched).

> **Check:** play. Walking in grass the HUD box says HIDDEN; in a shadow it only says HIDDEN while you stand still.

---

### Part 5: The house

The map below is the template's exact layout. Each character is one 16 px tile at `x = 16 × column`, `y = 16 × row`:

- `#` **masonry** (Brick, stone texture)
- `f` **furniture**: tables, the desk, shelves (Brick, wood texture)
- `h` **hedge** (Brick, hedge texture)
- `c` **coal heap** (Brick, coal texture)
- `g` **glass** (Brick, glass texture, **TAGS = glass**)
- `.` floor

```text
          11111111112222222222333333333344444444445555555555
012345678901234567890123456789012345678901234567890123456789
############################################################  0
############################################################  1
#..................##..ff..........ff..##.........g........#  2
#..................##..ff..........ff..##.........g........#  3
#..................##..ff..........ff..##.........g........#  4
#..................##..ff..ffffff..ff..##.........g........#  5
#...#####..#####.......ff..ffffff..ff..##.........g........#  6
#......................ff..........ff..##.........g........#  7
#..................##..ff..........ff..##.........g........#  8
#..................##..................##.........gggggg...#  9
#..................##..................##..................# 10
#..................##..................##..................# 11
#..................##..................##..................# 12
#..................##..................##..................# 13
#############################..##########ggggggg....ggggggg# 14
#############################..##########..................# 15
#.fffff............##..............#...##..................# 16
#..................##..............#...##..................# 17
#..................##....##....##..#...##..................# 18
#...fffff..........##....##....##..#..###..................# 19
#...fffff..........##..................##..................# 20
#......................................##..................# 21
#..........................................................# 22
#..................##......................................# 23
#...........fffff..##..................##..................# 24
#...........fffff..##....##....##......##..................# 25
#..................##....##....##......##..................# 26
#..................##..................##..................# 27
#..................##..................##..................# 28
#########..##################..##########gggggggggggggggggg# 29
#########..##################..##########gggggggggggggggggg# 30
#..................##......................................# 31
#..................##......................................# 32
#..................##.hhhhhh.....hhhhhh....hh..............# 33
#..................##.hhhhhh.....hhhhhh....hh..............# 34
#..................##......................hh..............# 35
#.............cccc.##......................hh...hhhhhhhh...# 36
#.............cccc.##......................hh...hhhhhhhh...# 37
#.............cccc.##.hhhh.........hhhh....hh..............# 38
#.............cccc.##.hhhh.........hhhh....hh..............# 39
#.............cccc.##.hhhh.........hhhh....hh..............# 40
#..................##.hhhh.........hhhh....hh...hhhhhhhh...# 41
#..................##...........................hhhhhhhh...# 42
#..................##......................................# 43
############################################################ 44
```

Build it with **Brush** (bottom toolbar): choose Brick, **SNAP = 16**, and drag over each run of the same letter. Make each rectangle as large as possible, and no bigger than one screen (20 × 15 tiles). Then:

- Set each piece's sprite to the right 16 × 16 texture with **Repeat as tiles** (save one of each as an entity and place copies).
- Give every **glass** piece the tag `glass`. Guard sight and Security cameras look straight through objects tagged glass, but Moth cannot walk through them. That is what makes the glasshouse tense: they can see you from the next room.
- Gaps to keep open: the study door at columns 29 to 30, row 14 (Part 8 puts the locked door there); the kitchen-to-coal-yard passage at columns 9 to 10, rows 29 to 30; the gallery-to-garden passage at columns 29 to 30, rows 29 to 30; the opening in the glass at columns 48 to 51, row 14.

---

### Part 6: Wardens

Every warden is a **Prowler** `12 × 16` with all its starter blocks removed and one **Guard sight** block. Start with these shared settings, then change what each warden's row says:

| Setting                     | Shared value                     |
| --------------------------- | -------------------------------- |
| Sees up to                  | 96                               |
| View angle                  | 70°                              |
| Time to spot you            | 0.7                              |
| Patrol speed                | 32                               |
| Chase speed                 | 74                               |
| Patrol route                | Stand guard and look around      |
| Route width / height        | 0 / 0                            |
| Faces at first              | Right                            |
| Looks around by             | 50°                              |
| Pauses at corners           | 1                                |
| Hears noises (×)            | 1                                |
| Shouts for help within      | 128                              |
| Knocked out from behind for | 14                               |
| When it catches the hero    | Lose a heart, back to checkpoint |

Draw the warden with `idle`, `move` (2 frames, 0.18 s) and `out` (lying down, used while knocked out). Save the first one as an entity.

| Warden                          | x, y     | Changes from the shared settings                                                 |
| ------------------------------- | -------- | -------------------------------------------------------------------------------- |
| Warden Pell (front garden)      | 338, 496 | Route Back and forth (left/right), Route width 256, Looks around 60°, Pauses 1.5 |
| Warden Hobb (east lawn)         | 754, 496 | Route Loop around a rectangle, 160 × 128, Patrol speed 28                        |
| Warden Quill (gallery)          | 354, 272 | Loop around a rectangle, 176 × 160, Patrol speed 30, Pauses 0.75                 |
| Warden Mott (study door)        | 466, 336 | Stand guard, Sees up to 88, Faces Up, Looks around 70°                           |
| Reserve warden A (barracks)     | 578, 256 | Stand guard, Sees up to 112, Chase speed 84, Faces Down, Looks around 30°        |
| Reserve warden B (barracks)     | 594, 272 | Same as A                                                                        |
| Warden Ivo (upper glasshouse)   | 658, 176 | Back and forth, Route width 112, Looks around 70°, Pauses 2                      |
| Warden Fenn (lower glasshouse)  | 674, 256 | Loop around a rectangle, 240 × 176, Patrol speed 30                              |
| Cook Brindle (kitchen)          | 34, 352  | Back and forth, Route width 240, Sees up to 88, Looks around 40°, Pauses 1.25    |
| Steward Ravel (study)           | 514, 112 | Stand guard, Sees up to 104, Faces Left, Looks around 70°                        |
| Warden Tull (vault antechamber) | 34, 176  | Back and forth, Route width 192                                                  |

A route starts where the warden stands: back and forth walks Route width to the right and back; a loop walks a rectangle of Route width × Route height clockwise from the warden's spot. Playtest to see the cones: each warden draws its sight cone while the game runs.

---

### Part 7: Front garden, east lawn and the barracks

- **Garden lamp:** **Checkpoint** `530, 672, 12 × 16`, keep **Checkpoint flag**. Lamps are where a caught Moth goes back to.
- **Moth's note:** Checkpoint `416, 672, 16 × 16`, remove Checkpoint flag, **Dialogue box** `Pause while open = Pause game`, `Show for = 5`. Lines (use **+ LINE**):
  1. `THREE STAR SEEDS, THEN OUT BY THE COAL CHUTE IN THE YARD. THE CHUTE IS PAST THE KITCHEN.`
  2. `HOLD X TO SNEAK: SLOW AND SILENT. WALKING IS HEARD, GRAVEL ALWAYS CRUNCHES.`
  3. `C THROWS A PEBBLE. WARDENS GO TO LOOK WHERE IT LANDS. YOU HAVE EIGHT.`
  4. `GRASS, CURTAINS AND FERNS HIDE YOU. SHADOWS HIDE YOU IF YOU KEEP STILL.`
  5. `BUMP A WARDEN FROM BEHIND TO KNOCK HIM OUT. IF ONE CATCHES YOU, BACK TO THE LAST LAMP.`
- **Night apple:** **Heart** `914, 690, 12 × 12`, Healing heart `1`.
- **Barracks portcullis:** **Cracked wall** `576, 304, 32 × 16`. Remove Dash breakable, keep Solid body, add **Switch door** `Channel = 2`. Iron bars sprite, Repeat as tiles. The alarm turns channel 2 on while it rings, which lifts the portcullis and lets the two reserve wardens out.
- **Barracks notice:** Checkpoint `544, 352`, Dialogue box (`Live gameplay`, `5 s`): `BARRACKS. THE PORTCULLIS LIFTS WHEN THE ALARM RINGS.`

---

### Part 8: The glasshouse (seed 1)

- **Glasshouse eye:** **Brick** `656, 32, 16 × 16`. Remove Solid body, add **Security camera**:

  | Setting             | Value              |
  | ------------------- | ------------------ |
  | Sees up to          | 150                |
  | View angle          | 45°                |
  | Points at           | 45° (down-right)   |
  | Sweeps across       | 80°                |
  | One sweep takes     | 6                  |
  | Time to spot you    | 0.7                |
  | When it spots you   | Call guards nearby |
  | Calls guards within | 320                |

  It does not ring the alarm; it sends the wardens to where it saw Moth.

- **Star seed: glasshouse:** **Core** `866, 66, 12 × 12`, keep **Collectible core** with `Points = 500`. Draw a seed with 2 glowing `idle` frames.

---

### Part 9: Kitchen, the key and the study (seed 2)

- **Kitchen lamp:** Checkpoint `274, 432, 12 × 16`.
- **Brass key:** **Core** `226, 418, 12 × 12`. Remove Collectible core (it must not count as a seed), add **Key pickup** `Key channel = 1`.
- **Study door:** **Brick** `464, 224, 32 × 32` in the gap in the wall. Remove Solid body, add **Locked door**: `Key channel = 1`, `Consume key = Consume key`. Door sprite.
- **Study lamp:** Checkpoint `530, 192, 12 × 16`.
- **Star seed: study:** Core `466, 50, 12 × 12`, Collectible core `500`.

#### The fuse box (a rule that turns a camera off)

1. **Brick** `416, 192, 16 × 16`, name **Fuse box**. Remove Solid body; it has no blocks at all.
2. Sprite with `idle` (fuses in) and `off` (fuses pulled).
3. Rule: `WHEN onCollision · TARGET self · IF Other has tag thief · DO Switch channel (3, on) ; Set state (off) ; Play animation (off) ; Send message (fuses)`.

   The **Other has tag thief** condition matters: without it, the floor under the fuse box touches it at the start and pulls the fuses before Moth gets there.

4. **Fuse label:** Checkpoint `400, 192`, Dialogue box (`Live gameplay`, `5 s`): `VAULT CAMERA FUSES. DO NOT TOUCH.`

---

### Part 10: The vault (seed 3)

- **Vault laser:** **Spikes** `318, 96, 4 × 32` across the vault doorway. Remove Hazard. Add:
  - **Alarm**: `Rings when = The hero touches it`, `Rings for = 15`, `Turns on channel while ringing = 2`, `Guards within = 0` (all).
  - **Blink**: `Visible for = 1.6`, `Hidden for = 1.4`, `Start offset = 0`. The beam blinks, so the player can time a dash through.

  Draw a red beam with 2 flickering frames, Repeat as tiles.

- **Vault eye:** **Brick** `288, 112, 16 × 16`, remove Solid body, add **Security camera**:

  | Setting                 | Value          |
  | ----------------------- | -------------- |
  | Sees up to              | 170            |
  | View angle              | 50°            |
  | Points at               | 180° (left)    |
  | Sweeps across           | 110°           |
  | One sweep takes         | 5              |
  | Time to spot you        | 0.5            |
  | When it spots you       | Ring the alarm |
  | Alarm rings for         | 15             |
  | Alarm turns on channel  | 2              |
  | Off while channel is on | 3              |

  `Off while channel is on = 3` is the wire to the fuse box: once Moth pulls the fuses, channel 3 is on and this camera goes dark.

- **Star seed: vault:** Core `146, 50, 12 × 12`, Collectible core `500`.

---

### Part 11: The coal yard (the exit)

- **Coal chute:** **Exit** `32, 640, 32 × 32`, keep **Locked exit**. It opens only when all three seeds (every Collectible core) are taken.
- **Chute sign:** Checkpoint `80, 656`, Dialogue box (`Live gameplay`, `5 s`): `COAL CHUTE. ALL THREE SEEDS, AND YOU ARE AWAY.`

---

### Part 12: Playtest the whole game

1. Front garden: sneak past Pell using the grass, or throw a pebble (C) to pull him away. Stay off the gravel.
2. Gallery: hide in the shadow, wait for Quill to loop past. Sneak over the creaky boards.
3. Glasshouse: move fern to fern; the camera only calls wardens, it does not raise the alarm. Seed 1.
4. Kitchen: wait for Brindle to turn, take the key from behind the tables.
5. Study: unlock the door, avoid Ravel's gaze, pull the fuses, seed 2.
6. Vault: time the laser, slip past Tull (or knock him out from behind), seed 3. The camera is off if you pulled the fuses.
7. Out through the kitchen to the coal chute.

Trip the laser once on purpose: the screen flashes, the HUD counts down, every warden hurries to the vault and the barracks portcullis opens.

#### Troubleshooting

| Problem                             | Fix                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------ |
| Guards see Moth through walls       | Walls must be Solid bodies; only objects tagged glass are see-through          |
| Guards cannot see through the glass | The glass pieces need the tag glass                                            |
| Moth is never hidden                | Hiding spots must not be solid, and Moth's middle must be inside the spot      |
| The fuse box fires at the start     | Its rule needs the condition Other has tag thief, and Moth needs the tag thief |
| The vault camera never switches off | Vault eye Off while channel is on = 3, and the fuse rule switches channel 3 on |
| The barracks never open             | The portcullis Switch door must use the same channel the alarm turns on (2)    |
| The chute stays shut                | The brass key must not be a Collectible core; check all three seeds are        |
| Moth is shoved when hit             | Damage + respawn Knockback = 0                                                 |

---

### Ideas to take it further

- Make lamps react to the alarm: a rule `WHEN onMessage, MESSAGE alarm` on a lamp can **Play animation** (a red glow), and `allclear` puts it back.
- Add a **Time limit** for an "escape before dawn" mode.
- Put a **Noise maker** in a **Timer** on a grandfather clock to pull wardens around on a schedule.
- Hide a **Treasure chest** with a second **Key input** item, like a smoke bomb built from **Invulnerability window** and **Particles**.

