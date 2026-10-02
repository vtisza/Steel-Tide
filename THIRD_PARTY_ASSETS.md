# Third-party assets

Steel Tide mixes its own procedural models and synthesised sounds with a small set of free assets.
Every asset below is **CC0 1.0** (public domain dedication) or, for fonts, the **SIL Open Font License 1.1**.
Both allow commercial use, modification and redistribution inside a game. CC0 needs no attribution, but the
authors are credited here and in the game's *Credits* screen anyway.

All files live in `res://assets/` and are loaded through `scripts/assets.gd`. Each loader call falls back
to the old procedural version if a file is missing, so the game still runs without them.

## Art direction

The target is the classic island-vs-island missile game, updated to a modern, clean low-poly look:

- **Keep the silhouettes.** Each structure keeps the shape it had before, so a player can still tell at a glance
  what a structure is: HQ dome or spike tower, cooling towers, tanks and drill, dish, gantry with missile,
  launcher pod, hangar, twin-barrel turret. The kit pieces replace the plain boxes under those shapes.
  They do not replace the shapes themselves.
- **Keep faction colour coding.** The kit's texture atlas is repainted at load time. The accent swatches become
  the team colour (blue for the player, red for the enemy), and the enemy's white hulls become charcoal. The
  procedural emblems (disc for the player, spike for the enemy) are still on every building.
- **Keep gameplay hooks.** Animated or scripted parts (`Spin`, `Core`, `Missile`, `ReadyLight`) are still separate
  nodes. The Resource Extractor's drill bit from the kit is moved under `Spin`, so it turns like the old drill.
- **One style family.** KayKit and Kenney both make flat-shaded, gradient-atlas low-poly art, which matches the
  existing procedural models. The effects use Kenney's cartoon smoke puffs rather than photographic sprites.

## Asset list

### 3D models: KayKit "Space Base Bits" 1.0

| | |
|---|---|
| Author | Kay Lousberg, <https://www.kaylousberg.com> |
| Source | <https://kaylousberg.itch.io/space-base-bits>, retrieved from the author's official repository <https://github.com/KayKit-Game-Assets/KayKit-Space-Base-Bits-1.0> (commit `6dfbcac9927d`) |
| License | CC0 1.0 Universal, see `assets/models/kaykit_space_base/LICENSE.txt` |
| Files | `assets/models/kaykit_space_base/*.gltf`, `*.bin`, `spacebits_texture.png` |
| Changes | Files unmodified. At runtime the original 1024 × 1024 atlas is team-recoloured (`Assets.kit_material`). |

Where each model is used:

| Model | Used for |
|---|---|
| `basemodule_E` (dome module) | Player Headquarters |
| `basemodule_A` | Enemy Headquarters base, under the procedural spike tower |
| `basemodule_B` | Power Plant control block, next to the procedural cooling towers |
| `basemodule_C` | Radar base |
| `basemodule_garage` | Mech Facility hangar |
| `drill_structure` | Resource Extractor drill rig (its `drill_module` spins) |
| `cargo_B_stacked`, `containers_A` | Resource Extractor storage |
| `containers_C`, `lights` | Missile Silo props and ready-light mast |
| `landingpad_small` | Interceptor Battery base |
| `rock_A`, `rock_B`, `rocks_A`, `rocks_B` | Coastal rocks and rubble of destroyed structures (neutral grey material) |

### Particle sprites: Kenney

| | |
|---|---|
| Author | Kenney, <https://www.kenney.nl> |
| License | CC0 1.0 Universal, see `assets/textures/particles/LICENSE.txt` |
| Changes | Renamed only. |

| File | Original | Retrieved from | Used for |
|---|---|---|---|
| `puff.png` | `sprites/smoke.png` | <https://github.com/KenneyNL/Starter-Kit-Racing> (commit `2f2e5f2646dd`) | Missile, interceptor and dropship trails, explosion smoke and fireball, damage smoke |
| `spark.png` | `sprites/particle.png` | <https://github.com/KenneyNL/Starter-Kit-3D-Platformer> (commit `3fa8a04b1c01`) | Muzzle flashes |
| `blob_shadow.png` | `sprites/blob_shadow.png` | <https://github.com/KenneyNL/Starter-Kit-FPS> (commit `185fd2326d74`) | Scorch mark under rubble |

### Decal texture: "Free Decals 01 – Sci-Fi" by Yughues

| | |
|---|---|
| Author | Yughues |
| Source | <https://opengameart.org/content/free-decals-01-sci-fi>, retrieved from the copy in <https://github.com/godotengine/godot-demo-projects> (`3d/decals/textures/scifi_1_albedo.png`, commit `15d4fcd70a42`) |
| License | CC0 1.0 Universal, see `assets/textures/decals/LICENSE.md` |
| Files | `assets/textures/decals/scifi_hatch.png` (renamed, otherwise unmodified) |
| Used for | Hexagonal launch hatch under the missile on every Missile Silo |

### Sound effects

| File | Author and source | License | Used for (Sfx key) |
|---|---|---|---|
| `toggle.ogg` | Kenney, [Starter Kit City Builder](https://github.com/KenneyNL/Starter-Kit-City-Builder) (commit `4535092b740b`) | CC0 | UI click (`click`) |
| `placement-a/b/c.ogg` | Kenney, Starter Kit City Builder | CC0 | Structure placed (`build`), random variant |
| `removal-a.ogg` | Kenney, Starter Kit City Builder | CC0 | Structure demolished (`demolish`) |
| `blaster.ogg` | Kenney, [Starter Kit FPS](https://github.com/KenneyNL/Starter-Kit-FPS) (commit `185fd2326d74`) | CC0 | Mech weapons (`mech_gun`) |
| `enemy_destroy.ogg` | Kenney, Starter Kit FPS | CC0 | Mech destroyed (`mech_down`) |
| `impact_big.wav` | FFeller, <https://freesound.org/people/FFeller/sounds/532873/>, trimmed copy from godot-demo-projects `3d/ragdoll_physics/sounds/` | CC0 | Heavy impact under missile hits and building destruction (`impact`) |

The licence notes are in `assets/audio/LICENSE.txt` and `assets/audio/impact_big.LICENSE.md`. All other sounds
(missile launch, alarms, radar ping, interceptor, explosions, victory and defeat) are still synthesised in
`scripts/sfx.gd`.

### Fonts (SIL Open Font License 1.1)

Retrieved from the Google Fonts repository <https://github.com/google/fonts> (`ofl/` directory, commit `23e54b51ddff`).
The OFL lets you bundle and embed the fonts in software, including commercial software, as long as the licence
text travels with them. The licence texts are in `assets/fonts/OFL-*.txt`, are exported inside the game pack,
and are copied into every release zip by `tools/build.sh`.

| File | Family | Designer | Used for |
|---|---|---|---|
| `BlackOpsOne-Regular.ttf` | Black Ops One | James Grieshaber, Eben Sorkin | Title and big banners (military stencil) |
| `ChakraPetch-Medium.ttf`, `ChakraPetch-Bold.ttf` | Chakra Petch | Cadson Demak | All HUD and menu text, 3D labels |
| `ShareTechMono-Regular.ttf` | Share Tech Mono | Carrois Type Design | Match statistics table |

## Generated in-engine (no files)

Some of the visual upgrade uses no third-party files:

- Water normal maps and shore foam: `NoiseTexture2D` normal maps and a shader in `scripts/island.gd`.
- Weathered concrete and terrain: a triplanar noise detail layer (`Island.detail_material`).
- Explosion glow and flash cards: a radial `GradientTexture2D` (`Fx.glow_texture`).

## Adding or replacing assets

1. Use only CC0, CC-BY or OFL assets, and prefer the author's own download or repository.
2. Put the files under `assets/<kind>/`, with the licence file next to them.
3. Add a row to this file: author, source URL (and commit, if it came from a repository), licence, changes, and use.
4. For CC-BY assets, also add the attribution to `CREDITS` in `scripts/main_menu.gd`. CC-BY requires it.
5. Load the file through `Assets` so the game keeps a fallback.
6. Check the look with `godot --path . res://tests/asset_showcase.tscn -- --shotdir=/tmp/shots`, which saves
   screenshots of every structure for both factions, plus combat and explosions.

Sources checked but not used: the Kenney "City Builder" and "Basic Scene" models (too civilian or fantasy),
KayKit "City Builder Bits" and "Prototype Bits" (off-theme), and the textures in Godot's material-tester demo
(no explicit licence).


## September 2026 graphics rework — offshore fortresses

The visual direction is weathered naval infrastructure: desaturated petrol-blue and
ivory player hulls, oxide-red and charcoal enemies, dark segmented decks, warm
hazard paint, cyan/amber navigation lights and a subdued teal sea. Existing unit
silhouettes, team emblems, animation node names and footprints remain intact.

### High-definition surface maps: ambientCG Concrete030

- Author: ambientCG / Lennart Demes.
- Official source: https://ambientcg.com/view?id=Concrete030 (checked 2026-09-26).
- Archive: https://ambientcg.com/get?file=Concrete030_2K-JPG.zip.
- License: **CC0 1.0 Universal**, verified at https://docs.ambientcg.com/license/.
  Commercial use and redistribution of source textures are permitted.
- Files: `assets/textures/concrete/Concrete030_2K-JPG_{Color,NormalGL,Roughness}.jpg`.
  All three maps are **2048 × 2048**, unmodified; hashes and provenance accompany
  them in `assets/textures/concrete/LICENSE.md` and ship in release license folders.
- Used on building foundations, cooling towers, island retaining walls, and decks.
  Triplanar mapping preserves scale across differently sized foundations; deck
  materials use the color and OpenGL normal maps, with procedural panel seams and
  fasteners. Normal intensity is restrained to keep distant units readable.
- Only necessary maps are included (~14 MB source); no unused displacement maps,
  DCC scenes, or preview images. Mipmapped anisotropic sampling reduces shimmer.

### Original geometry and shader work

`Models.armor_mesh` creates cached chamfered armor meshes; `Island._build_perimeter`
creates modular seawalls, hazard markings and navigation lights; and
`assets/shaders/fortress_deck.gdshader` creates anti-aliased panel joints and bolts.
These are original project code/geometry with no external source or additional
third-party license requirement. No AI-generated raster images were used.

The ocean shader now blends encoded normal maps without normalizing RGB values,
uses ordered smoothstep bounds, and has narrower, quieter surf. The denser coastal
mesh reduces jagged beaches. Lighting has a warmer, lower sun and restrained bloom;
Forward+ adds contact shading through SSAO, while Compatibility retains the same
geometry, textures and readable palette without that optional effect.

### Search and selection rationale

The official KayKit Space Base Bits page was rechecked:
https://kaylousberg.itch.io/space-base-bits confirms CC0 and a 1024px gradient atlas.
Its consistent silhouettes remain a better fit for this grid strategy game than
mixing unrelated realistic building packs. The original atlas resolution is now
preserved instead of reducing it to 256px. ambientCG Concrete030 was selected for
neutral, fine detail that supports this kit without overwhelming its forms.
New deck and seawall geometry was authored specifically for the game's grid.
