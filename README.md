# Minecraft Resourcepack & Texturepack Creator & Linter Skill

[![Minecraft Version](https://img.shields.io/badge/Minecraft%20Java-1.20.2%20--%2026.3%2B-5b8c32.svg)](https://minecraft.net)
[![Resource Pack Format](https://img.shields.io/badge/Resource%20Pack%20Format-18%20--%2097.1-orange.svg)](https://minecraft.net)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An architectural, highly-specialized AI Agent Skill designed for **Google Antigravity**, Claude Code, and agentic pairing. It creates, audits, lints, and optimizes Minecraft Java Resourcepacks (Texturepacks, 3D Block & Item Models, Sounds, Fonts, Equipment Assets, and Post-Effects Shaders) across all definitive releases from **1.20.2 up to 26.3+**.

---

## 🏗️ Architecture: Invariant Laws & Version Add-on Modules

1. **The Invariant Laws (`SKILL.md`)**:
   - Universal graphical and asset standards for Minecraft resource packs.
   - Enforces **Strict JSON** across all model, blockstate, atlas, and sound files.
   - Texture rules: 32-bit PNG with clean alpha, powers of two, vertical animation strips with paired `.mcmeta`.
   - Audio rules: Strict **Ogg Vorbis (`.ogg`)** format; **Mono** audio mandatory for 3D positional sound events, stereo reserved for UI/music, and `"stream": true` for long audio tracks.
   - Visual Branding: Strict **Modrinth Minimalist pack.png style** (isometric 2.5D clean dark lineart, soft pastel cel-shading, floating iconic subjects, no terrain base, no generic text, dark indigo background).
2. **The Version Add-on Engine (`references/versions/`)**:
   - Manages version transitions (from 1.20.2 up to 26.3+).
   - Tracks breaking asset migrations:
     - 1.21.2: **Equipment Assets** (`assets/<ns>/equipment/`) replacing legacy armor textures.
     - 1.21.6: **Universal Strict JSON** validation.
     - 1.21.9: Decimal pack formats (`69.0`), sprite components in text.
     - 26.3: **Custom Post-Effects Shaders** (`shaders/post/`) accessible via `/posteffect`, `shade_direction_override` in block models, trim palette restructuring.

---

## 📋 Compatibility Matrix & Supported Versions

| Minecraft Version | Resource Pack Format | Data Pack Corrispondente | Milestone Features | Version Module |
|---|---|---|---|---|
| **26.3** | `97.1` | `121.0` | Custom post-effects shaders (`/posteffect`), OIT shaders, `shade_direction_override`, palette texture restructuring (`textures/palettes/trim/`) | [`v26_3.md`](references/versions/v26_3.md) |
| **26.2** | `88.0` | `107.1` | Core shaders modernization, sprite atlas cleanup | [`v26_1_to_26_2.md`](references/versions/v26_1_to_26_2.md) |
| **26.1** | `84.0` | `101.1` | GPU chunk rendering overhaul, generated default sprites, animal sound variants | [`v26_1_to_26_2.md`](references/versions/v26_1_to_26_2.md) |
| **1.21.11** | `75.0` | `94.1` | Zombie Nautilus textures, models, and sound events | [`v1_21_11.md`](references/versions/v1_21_11.md) |
| **1.21.9 - 1.21.10** | `69.0` | `88.0` | Minor decimal pack formats (`69.0`), `sprite` text component, Mannequin entity textures | [`v1_21_6_to_1_21_10.md`](references/versions/v1_21_6_to_1_21_10.md) |
| **1.21.6** | `63` | `80` | **Universal Strict JSON** across all pack files, modal dialog sprites (`show_dialog`) | [`v1_21_6_to_1_21_10.md`](references/versions/v1_21_6_to_1_21_10.md) |
| **1.21.5** | `55` | `71` | Firefly & tinted_leaves particles atlases, UI sprite refinements | [`v1_21_4_to_1_21_5.md`](references/versions/v1_21_4_to_1_21_5.md) |
| **1.21.4** | `46` | `61` | Winter Drop (Pale Garden, Creaking, Resin, Eyeblossom) textures and models | [`v1_21_4_to_1_21_5.md`](references/versions/v1_21_4_to_1_21_5.md) |
| **1.21.2 - 1.21.3** | `42` | `57` | **Equipment Assets Revolution** (`equipment/`), colored Bundles, model tint sources | [`v1_21_2_to_1_21_3.md`](references/versions/v1_21_2_to_1_21_3.md) |
| **1.21.0 - 1.21.1** | `34` | `48` | Tricky Trials assets (Crafter UI, Vault, Mace, Wind Charge, Jukebox sound events) | [`v1_21_0_to_1_21_1.md`](references/versions/v1_21_0_to_1_21_1.md) |
| **1.20.5 - 1.20.6** | `32` | `41` | Wolf armor textures & colorable overlay, Armadillo, particle atlases | [`v1_20_5_to_1_20_6.md`](references/versions/v1_20_5_to_1_20_6.md) |
| **1.20.2 - 1.20.4** | `18` / `22` | `18` / `26` | Multi-pack overlays in `pack.mcmeta`, GUI sprites 9-slice scaling, font providers | [`v1_20_2_to_1_20_4.md`](references/versions/v1_20_2_to_1_20_4.md) |

---

## 🚀 How to Install & Use

### 1. In Google Antigravity / Gemini CLI
Clone or copy this folder into your custom skills directory:
```bash
git clone https://github.com/Manolo006/minecraft-resourcepack-skill.git ~/.gemini/config/skills/minecraft-resourcepack-dev
```

### 2. In Claude Code / Other Agentic Tools
```bash
git clone https://github.com/Manolo006/minecraft-resourcepack-skill.git ~/.claude/skills/minecraft-resourcepack
```

---

## 📄 License
Released under the [MIT License](LICENSE).
