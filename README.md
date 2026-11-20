# Assets for AI agents

A small, curated asset pack for AI coding agents that build 3D scenes and games: PBR
textures, HDRIs, sound effects and a rigged hand model — everything an agent needs when it
has no artistic pipeline of its own.

Every file is reachable by a **raw URL**, so an agent can `curl` it straight into a project
without cloning the repo.

## Contents

**PBR materials (2K, 8192 source, JPG + EXR)**

| id | material | set |
| --- | --- | --- |
| `tltleibaw` | Old Hospital Concrete Floor — worn, chipped paint, 1×1 m | Albedo, Normal, Roughness, AO, Displacement (8-bit JPG + 32-bit EXR) |
| `vcigedc` | Concrete Pavement — old Japanese street slabs, seams, grime, 2×2 m | Albedo, Normal, Roughness, AO, Displacement |

Each material ships a `*.json` with tags, category, physical size and preview path, plus a
720×720 `*_Preview.png`.

**Environment**

- `kloppenheim_06_puresky_4k.hdr` — clear sky HDRI, 4K
- `mud_road_puresky_4k.hdr` — open mud road HDRI, 4K

**Audio (WAV)**

- Player footsteps: 4 × concrete, 4 × dirt
- Pistol: `empty`, `fire2`, `fire3`, `reload1`
- `industrial_ambient_1.wav` — industrial ambience loop

**Models**

- `hand_with_gloves.glb` — gloved hand, glTF 2.0

## Usage

`RESOURCES.txt` is the manifest: it lists every file with type, size and description, and
the raw base URL to build links from.

```bash
BASE=https://raw.githubusercontent.com/Gl1ch5/assets-for-ai-agents/main
curl -O $BASE/tltleibaw_2K_Albedo.jpg
curl -O $BASE/hand_with_gloves.glb
```

Point an agent at `RESOURCES.txt` and it can pick assets by keyword instead of guessing
filenames.

## Notes

- Textures are trimmed to 2K for repo size; the 8K originals stay offline.
- The normal maps are OpenGL-convention — flip the green channel for DirectX engines.
- Check the licence of each source before shipping anything commercially.