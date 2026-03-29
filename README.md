# BMW R1200GS Adventure — 3D Configurator

An immersive browser-based 3D configurator for the BMW R1200GS Adventure, built with [Three.js](https://threejs.org/).

**[Live Demo →](https://YOUR-USERNAME.github.io/YOUR-REPO-NAME)**

![Configurator Preview](preview.png)

## Features

- Full 3D model with HDR environment lighting
- 4 paint colour variants with animated transitions
- 2 geometry variants (Standard / Adventure)
- Camera presets: 3/4, Front, Side, Top
- Auto-rotate with drag-to-orbit & scroll-to-zoom
- Zero build step — pure HTML + ES modules

## Assets

| File | Size | Notes |
|------|------|-------|
| `BMW_BIke_configurator_1.glb` | ~105 MB | Draco-compressed GLTF model (Git LFS) |
| `neon_photostudio_4k.hdr` | ~24 MB | HDR environment map (Git LFS) |
| `configurator_bike.json` | 15 KB | Colour & geometry variant config |
| `index.html` | ~30 KB | Self-contained configurator |

> Large files (`.glb`, `.hdr`) are stored via **Git LFS**. Make sure you have [Git LFS installed](https://git-lfs.github.com/) before cloning.

## Local Development

```bash
# Clone (requires Git LFS)
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME

# Serve locally (any static server works)
npx serve .
# then open http://localhost:3000
```

> Opening `index.html` directly via `file://` won't work — browsers block cross-origin requests.

## GitHub Pages Deployment

1. Push to GitHub
2. Go to **Settings → Pages**
3. Set Source to **Deploy from a branch → main → / (root)**
4. Save — your site will be live at `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME`

> **Note:** GitHub Pages works with Git LFS. The `.glb` and `.hdr` files will be served correctly.

## Config Format

`configurator_bike.json` drives all variant logic:

```json
{
  "groups": [
    {
      "id": "colour_varaint",
      "type": "COLOR",
      "variants": [
        {
          "id": "color_2",
          "hex": "#050C33",
          "target_objects": ["MeshName_001", "..."],
          "mat_slot": 0
        }
      ]
    },
    {
      "id": "geo_variant",
      "type": "GEO",
      "variants": [
        {
          "id": "variant_1",
          "objects": ["GeoMeshName_001", "..."]
        }
      ]
    }
  ]
}
```

- **COLOR group** — lists meshes whose material slot 0 colour is overridden
- **GEO group** — lists mutually exclusive mesh sets that are shown/hidden

## Tech Stack

- [Three.js r167](https://threejs.org/) via ESM import map (no bundler)
- `GLTFLoader` + `DRACOLoader` for compressed GLTF
- `RGBELoader` for HDR environment
- `OrbitControls` for camera interaction
- Pure CSS glass-morphism UI

## License

3D model © respective owner. Configurator code MIT.
