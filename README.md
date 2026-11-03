# VESTRA — Personal 3D Avatar & Smart Styling Advisor

**Turn your measurements into a 3D you — then try on the whole wardrobe before you buy.**

VESTRA is a fully client-side styling advisor. Enter your body measurements and appearance
preferences, and it builds a personalized 3D white model, diagnoses your body shape, and
generates coordinated outfit / hairstyle / style / makeup advice — with a live virtual
try-on where garments, colours and patterns are rendered directly on your avatar.

No install. No backend. No build step. Open `index.html` and go.

---

## ✨ Features

- **Parametric body modeling** — height, weight, bust / waist / hip and shoulder width drive
  the mesh, so proportions follow *your* numbers instead of a fixed template.
- **Real-time 3D viewport** — drag to rotate, scroll to zoom, right-click to pan; toggle
  skin tone / white model, auto-rotate, reset view, one-click snapshot export.
- **Body-shape diagnosis** — an automatic silhouette classification with numeric metrics,
  so every recommendation is grounded in your actual proportions.
- **Four advice engines** — outfit, hairstyle, style and makeup tabs, powered by a
  deterministic rule engine that works completely offline.
- **Virtual try-on** — swap tops, bottoms and complete looks on the avatar; recolour from a
  preset palette or a custom picker; apply patterns live on the mesh.
- **Seasonal wardrobe** — six complete looks pre-rendered on the white model.
- **Optional AI layer** — plug in any OpenAI-compatible endpoint (e.g. DeepSeek) for deeper,
  free-text styling commentary. No key? The built-in rules answer instead.

## 🧭 How it works

```
Input (11 fields) → Parametric body build → Shape diagnosis → Advice (4 tabs) → Virtual try-on
                                        ↘ optional LLM commentary ↗
```

| Stage | What happens |
|-------|--------------|
| **I · Input** | Gender, height, optional weight, bust, waist, hip, shoulder width + face shape, skin tone, style preference |
| **II · Build** | A parametric white model is constructed in three.js; an optional Hunyuan-3D GLB mesh replaces it when available |
| **III · Diagnose** | The silhouette is classified and returned with numeric metrics |
| **IV · Try on** | Looks, colours and patterns are applied live in the viewport |

## 📐 Input specification

| Group | Field | Type | Range / options |
|-------|-------|------|-----------------|
| Basic | `gender` | Toggle | female · male |
| | `height` | Number | 140 – 220 cm |
| | `weight` | Optional | 30 – 200 kg |
| Circumference | `bust` | Number | 50 – 180 cm |
| | `waist` | Number | 40 – 180 cm |
| | `hip` | Number | 50 – 200 cm |
| | `shoulder` | Number | 25 – 70 cm |
| Appearance | `face` | Select | oval · round · square · heart · long |
| | `skin` | Select | cool · warm · neutral · tan · deep |
| | `style` | Select | minimal · sweet · elegant · casual · edgy |

## 🛠 Tech stack

- **Rendering** — three.js r128 over WebGL, with a 3-tier CDN fallback chain
- **Geometry** — parametric body construction + GLTFLoader for Hunyuan-3D GLB meshes
- **Logic** — vanilla JavaScript rule engine, no framework
- **AI (optional)** — OpenAI-compatible chat completion API

## 🚀 Getting started

```bash
git clone https://github.com/<your-username>/vestra.git
cd vestra
# then just open index.html in your browser
```

Or double-click `index.html` — that's it.

**Optional:** to enable AI deep advice, open the "AI Settings" panel in the page and fill in
your OpenAI-compatible base URL, API key and model name.

## 📁 Project structure

```
vestra/
├── index.html            # entry point & page layout
├── css/
│   └── style.css         # styling
└── js/
    ├── GLTFLoader.js     # GLB mesh loading (Hunyuan-3D export)
    ├── bodyModel.js      # embedded white-model data (optional, auto-fallback)
    ├── bodyBuilder.js    # parametric body construction
    ├── recommendations.js# rule-based advice engine
    └── app.js            # app logic, 3D viewport & try-on
```

## ⚠️ Disclaimer

The avatar is parametrically inferred, not 3D-scanned; fabric drape is visualised, not
physically simulated. All advice is for styling reference only — actual fit depends on the
real garment.

## 📄 License

Released under the [MIT License](LICENSE).
