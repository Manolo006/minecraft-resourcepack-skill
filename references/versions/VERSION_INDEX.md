# Indice Versioni & Matrice Resource Pack (Texturepack)

Questo indice funge da matrice ufficiale per il versioning dei Resourcepack (Texturepack) in Minecraft Java Edition.
La skill opera con il modello **Leggi Immutabili + Moduli Add-on per Versione**.

---

## Tabella Formati Resource Pack

| Versione Minecraft | Resource Pack Format | Data Pack Corrispondente | Milestone Grafica / Asset | Modulo Tecnico |
|---|---|---|---|---|
| **26.3** | `97.1` | `121.0` | **Custom Post-Effects Shaders** (`/posteffect`), OIT Shaders, rimozione `shade` nei block models (`shade_direction_override`), palette texture in `textures/palettes/trim/` | [`v26_3.md`](v26_3.md) |
| **26.2** | `88.0` | `107.1` | Core Shaders aggiornati per backend grafico moderno, pulizia atlas sprite | [`v26_1_to_26_2.md`](v26_1_to_26_2.md) |
| **26.1** | `84.0` | `101.1` | Nuovo rendering GPU dei chunk, sprite di default generati, sound variants per animali | [`v26_1_to_26_2.md`](v26_1_to_26_2.md) |
| **1.21.11** | `75.0` | `94.1` | Asset texture e audio per Zombie Nautilus, aggiornamento font provider | [`v1_21_11.md`](v1_21_11.md) |
| **1.21.9 - 1.21.10** | `69.0` | `88.0` | **Formati decimali (`69.0`)**, sprite GUI e item nei testi (`sprite`), texture e pose Mannequin | [`v1_21_6_to_1_21_10.md`](v1_21_6_to_1_21_10.md) |
| **1.21.6** | `63` | `80` | **Strict JSON Universale** per modelli e atlanti, sprite UI dialoghi modali (`show_dialog`) | [`v1_21_6_to_1_21_10.md`](v1_21_6_to_1_21_10.md) |
| **1.21.5** | `55` | `71` | Texture particelle `firefly` e `tinted_leaves`, aggiornamenti sprite GUI | [`v1_21_4_to_1_21_5.md`](v1_21_4_to_1_21_5.md) |
| **1.21.4** | `46` | `61` | Texture Winter Drop (Pale Garden, Creaking, Resin, Eyeblossom), modelli foglie | [`v1_21_4_to_1_21_5.md`](v1_21_4_to_1_21_5.md) |
| **1.21.2 - 1.21.3** | `42` | `57` | **Equipment Assets**: cartella `assets/<ns>/equipment/` sostituisce le texture legacy delle armature; tint sources | [`v1_21_2_to_1_21_3.md`](v1_21_2_to_1_21_3.md) |
| **1.21.0 - 1.21.1** | `34` | `48` | Texture Tricky Trials (Crafter, Trial Spawner, Vault, Mace, Wind Charge, Ominous Vault) | [`v1_21_0_to_1_21_1.md`](v1_21_0_to_1_21_1.md) |
| **1.20.5 - 1.20.6** | `32` | `41` | Texture e armature per Lupi (Wolf Armor), Armadilli, atlanti particelle | [`v1_20_5_to_1_20_6.md`](v1_20_5_to_1_20_6.md) |
| **1.20.3 - 1.20.4** | `22` | `26` | Texture atlanti per `dust_plume` e `white_smoke`, formattazione stringhe font | [`v1_20_2_to_1_20_4.md`](v1_20_2_to_1_20_4.md) |
| **1.20.2** | `18` | `18` | Overlays multi-pack in `pack.mcmeta`, interpolazione display entities, slicing texture GUI | [`v1_20_2_to_1_20_4.md`](v1_20_2_to_1_20_4.md) |

---

## Regole di Risoluzione della Skill
1. **Default**: In assenza di specifica dell'utente, la skill imposta **Minecraft 26.3** (`pack_format: 97.1`).
2. **Adattamento Automatico**: La skill verifica o converte automaticamente la cartella degli asset:
   - Se versione >= `42` (1.21.2+): usa la cartella `assets/<ns>/equipment/` per le armature.
   - Se versione >= `63` (1.21.6+): applica Strict JSON a ogni file `.json` nei modelli e atlanti.
   - Se versione >= `97.1` (26.3+): sposta le palette trim in `textures/palettes/trim/` e supporta gli shader post-processing in `shaders/post/`.
