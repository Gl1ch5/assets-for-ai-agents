# Assets for AI agents

A small, curated asset pack for AI coding agents that build 3D scenes, games and level
prototypes: PBR textures, HDRIs, sound effects, a glTF hand and one full Assetto Corsa car
model. Every file is reachable by a **raw URL**, so an agent can `curl` it straight into a
project without cloning anything.

**Base URL:** `https://raw.githubusercontent.com/Gl1ch5/assets-for-ai-agents/main/`

## Prompt for your agent

Paste everything below into your agent (Claude Code, Codex, Cursor, a Telegram agent — any
of them). It is self-contained: rules, exact filenames, sizes and what each file is.

```text
You have a game-asset pack available over plain HTTPS. Base URL for every file:

https://raw.githubusercontent.com/Gl1ch5/assets-for-ai-agents/main/

Download only what you need with curl/wget straight from the raw URL — never open the
/blob/ page, it returns HTML.

Rules:
1. Keep downloaded binaries out of the project repo (use assets/ or a cache dir).
2. Albedo is sRGB. Normal, Roughness, AO and Displacement are linear (non-color).
3. Normal maps are OpenGL convention — flip the green channel for DirectX/Unreal.
4. PBR materials have a real-world size: tltleibaw is 1x1 m, vcigedc is 2x2 m. Tile UVs
   to match, otherwise the texture scale will look wrong.
5. Displacement ships twice: .jpg is an 8-bit preview, .exr is 32-bit float (use the EXR
   for real displacement or nanite-style detail).
6. Textures are 2K (originals were 8K). They are seamless where the source was seamless;
   tltleibaw and vcigedc are tested for tiling, image_301e3b7 is not.
7. Sound files are WAV at the sizes below. For footsteps pick a random variant from the
   matching surface group so the steps do not repeat.
8. viper_srt.rar is an Assetto Corsa car mod, not a glTF asset — do not try to load it in a
   web or Godot scene without converting the KN5 first.

=== PBR MATERIAL 1: "Old Hospital Concrete Floor" (id tltleibaw) ===
Worn abandoned-hospital concrete floor, dirty, chipped paint, 1x1 m, 2K. Archviz, games, VFX.
  tltleibaw_2K_Albedo.jpg             3.7 MB  base color, sRGB
  tltleibaw_2K_Normal.jpg             6.9 MB  normal map, OpenGL
  tltleibaw_2K_Roughness.jpg          2.1 MB  roughness, linear
  tltleibaw_2K_AO.jpg                 1.5 MB  ambient occlusion, linear
  tltleibaw_2K_Displacement.jpg       632 KB  height, 8-bit preview
  tltleibaw_2K_Displacement.exr      12.9 MB  height, 32-bit float EXR (PIZ), 2048x2048
  tltleibaw.json                       42 KB  metadata: tags, category, physical size, preview
  Floors_Concrete_tltleibaw_surface_Preview.png    1017 KB  preview 720x720

=== PBR MATERIAL 2: "Concrete Pavement" (id vcigedc) ===
Old Japanese street concrete: grey slabs, seams, grime, 2x2 m, 2K. Exterior, urban/rural.
  vcigedc_2K_Albedo.jpg               4.9 MB  base color, sRGB
  vcigedc_2K_Normal.jpg               6.8 MB  normal map, OpenGL
  vcigedc_2K_Roughness.jpg            1.8 MB  roughness, linear
  vcigedc_2K_AO.jpg                   2.4 MB  ambient occlusion, linear
  vcigedc_2K_Displacement.jpg         534 KB  height, 8-bit preview
  vcigedc_2K_Displacement.exr        12.8 MB  height, 32-bit float EXR (PIZ), 2048x2048
  vcigedc.json                         41 KB  metadata: tags, color, country, size, preview
  Concrete_Slab_vcigedc_surface_Preview.png    1012 KB  preview

=== SINGLE TEXTURE: pool mosaic ===
  image_301e3b7.jpg                   1.1 MB  blue glass mosaic tiles with water highlights, 1024x1024, no metadata,
                                             seamless not verified

=== 3D MODEL ===
  hand_with_gloves.glb                8.2 MB  glTF 2.0 binary, gloved hand (first-person viewmodel);
                                             embedded textures/animations not verified

=== HDRIs (equirectangular, 4K, Radiance .hdr) ===
  kloppenheim_06_puresky_4k.hdr      16.6 MB  clear sky, for lighting and background
  mud_road_puresky_4k.hdr            15.7 MB  clear sky over a dirt road, 4K

=== SFX: player footsteps (WAV) ===
  Player_player_footsteps_concrete1.wav     42 KB  step on concrete, variant 1
  Player_player_footsteps_concrete2.wav     54 KB  step on concrete, variant 2
  Player_player_footsteps_concrete3.wav     62 KB  step on concrete, variant 3
  Player_player_footsteps_concrete4.wav     38 KB  step on concrete, variant 4
  Player_player_footsteps_dirt1.wav     43 KB  step on dirt, variant 1
  Player_player_footsteps_dirt2.wav     74 KB  step on dirt, variant 2
  Player_player_footsteps_dirt3.wav     74 KB  step on dirt, variant 3 (same size as dirt2, may be a duplicate)
  Player_player_footsteps_dirt4.wav     53 KB  step on dirt, variant 4

=== SFX: pistol (WAV) ===
  Player_weapons_pistol_pistol_fire2.wav     137 KB  gunshot, variant 2
  Player_weapons_pistol_pistol_fire3.wav     104 KB  gunshot, variant 3
  Player_weapons_pistol_pistol_empty.wav       7 KB  empty magazine click
  Player_weapons_pistol_pistol_reload1.wav     41 KB  reload, variant 1
  (there is no fire1 — do not reference it)

=== SFX: ambience (WAV) ===
  industrial_ambient_1.wav            684 KB  industrial background ambience, loop not verified

=== CAR MOD (Assetto Corsa, not glTF) ===
  viper_srt.rar                      21.1 MB  VIPER_SRT Assetto Corsa car: KN5 body/collider, data/*.ini (aero, ai,
                                             brakes, car, cameras), textures, steer animation

Example:
  curl -O https://raw.githubusercontent.com/Gl1ch5/assets-for-ai-agents/main/tltleibaw_2K_Albedo.jpg

Full manifest with the same data: RESOURCES.txt

## Asset index

| file | type | size | what it is |
| --- | --- | --- | --- |
| `tltleibaw_*` | PBR material | 2K set | Old Hospital Concrete Floor, 1×1 m |
| `vcigedc_*` | PBR material | 2K set | Concrete Pavement, 2×2 m |
| `image_301e3b7.jpg` | texture | 1.1 MB | blue pool-tile mosaic, 1024² |
| `hand_with_gloves.glb` | model | 8.2 MB | gloved hand, glTF 2.0 |
| `kloppenheim_06_puresky_4k.hdr` | HDRI | 17 MB | clear sky, 4K |
| `mud_road_puresky_4k.hdr` | HDRI | 16 MB | sky over dirt road, 4K |
| `Player_player_footsteps_*` | SFX | 8 files | concrete 1–4, dirt 1–4 |
| `Player_weapons_pistol_*` | SFX | 4 files | fire2, fire3, empty, reload1 |
| `industrial_ambient_1.wav` | SFX | 700 KB | industrial ambience |
| `viper_srt.rar` | Assetto Corsa mod | 22 MB | VIPER_SRT car (KN5 + ini + textures) |

34 asset files in total (plus this README and `RESOURCES.txt`).

## Notes

- Textures are trimmed to 2K for repo size; the 8K originals stay offline.
- Normal maps are OpenGL convention — flip green for DirectX engines.
- Check the licence of each source before shipping anything commercially.
