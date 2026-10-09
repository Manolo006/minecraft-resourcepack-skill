---
name: minecraft-resourcepack
description: >
  Skill architetturale specializzata per creare, verificare, strutturare e ottimizzare
  Resourcepack e Texturepack per Minecraft Java (da 1.20.2 a 26.3+). Gestisce modelli 3D,
  texture, animazioni .mcmeta, suoni, font, equipment assets, shaders post-effect e icone pack.png.
---

# Minecraft Resourcepack Master Skill: Leggi Immutabili & Moduli Versionati

Questa skill opera come un **Linter Severo** e un **Architetto di Texturepack e Risorse Visive/Audio**.
È strutturata su due livelli gerarchici:
1. **La Legge Immutabile**: Standard grafici, sonori, strutturali e di formato validi per qualsiasi resource pack moderno.
2. **Il Motore dei Moduli Add-on**: Variazioni specifiche per versione (da 1.20.2 fino a 26.3+) consultabili in `references/versions/`.

---

## PARTE 1: LE LEGGI IMMUTABILI DEI RESOURCEPACK

### Legge 1: Struttura Radice & Isolamento Asset
- Radice obbligatoria: `pack.mcmeta`, `pack.png` e la cartella `assets/<namespace>/`.
- **Namespace Vanilla (`assets/minecraft/`)**: Si usa ESCLUSIVAMENTE per sovrascrivere o rimpiazzare texture, modelli, suoni o lingue native del gioco.
- **Namespace Custom (`assets/<tuo_namespace>/`)**: Si usa SEMPRE per modelli custom, texture personalizzate o risorse richiamate da datapack (es. tramite `item_model`, `equipment`, o `sounds.json`).

### Legge 2: Regola di Stile Grafico Minecraft per `pack.png`
L'icona del pacchetto (`pack.png`, dimensione 64x64 o 128x128 pixel) DEVE rispettare rigorosamente il seguente stile:
- **Stile Modrinth Minimale**: Grafica vettoriale isometrica / 2.5D con contorni netti scuri (lineart blu scuro/ardesia) e ombreggiatura cell-shading morbida a toni pastello.
- **Soggetti Iconici Fluttuanti al Centro**: Solo gli elementi chiave al centro (es. manichini, strumenti, cubi stilizzati).
- **NESSUNA Base di Terreno**: Niente blocchi di terra, erba, pedane o diorami complessi.
- **NESSUN Testo o Titolo**: Mai inserire scritte generiche (come "TEXTURE", "MOD", "PACK" o titoli).
- **Sfondo Uniforme o Gradiente Radiale**: Tonalità blu/indaco scuro (`#232247` / `#2c2c54`).

### Legge 3: Standard Tecnico delle Texture e Animazioni
- **Formato File**: Rigorosamente file `.png` a 32-bit con canale alpha trasparente pulito.
- **Dimensioni**: Potenze di 2 preferite (`16x16`, `32x32`, `64x64`, `128x128`, `256x256`).
- **Texture Animate**:
  - Le animazioni si sviluppano in **un'unica striscia verticale** (`larghezza x (larghezza * numero_frame)`).
  - Obbligo del file di metadata affiancato: `<nome_texture>.png.mcmeta`.
  - Schema minimo:
    ```json
    {
      "animation": {
        "frametime": 2,
        "interpolate": true
      }
    }
    ```

### Legge 4: Audio e Suoni (`sounds.json`)
- **Formato Obbligatorio**: Tutti i file audio DEVONO essere in formato **Ogg Vorbis (`.ogg`)**.
- **Canale Audio Mono vs Stereo**:
  - **Suoni 3D Posizionali**: DEVONO essere rigorosamente **MONO** a 1 canale! In Minecraft Java, qualsiasi audio stereo viene riprodotto senza attenuazione 3D e risuona a volume identico in tutto il mondo indipendentemente dalla distanza della sorgente.
  - **Musica di Sottofondo e UI**: Possono essere **STEREO**.
- **Streaming Audio**: La musica, i dischi jukebox e i brani lunghi DEVONO avere `"stream": true` in `sounds.json` per evitare memory leak e lag spike di decompressione RAM.

### Legge 5: Modelli 3D (`models/`) e Strict JSON
- Tutti i file `.json` in `models/block/` e `models/item/` devono rispettare la validazione Strict JSON (niente virgole finali, niente commenti).
- Coordinate degli elementi (`from`, `to`): comprese tra `-16` e `32` per blocchi standard.
- Texture mapping: prefisso `#` per le variabili di texture (es. `"textures": {"layer0": "minecraft:item/iron_sword"}`).

---

## PARTE 2: MOTORE DEI MODULI ADD-ON PER VERSIONE

La skill consulta l'indice di compatibilità in [references/versions/VERSION_INDEX.md](references/versions/VERSION_INDEX.md) e attiva il modulo idoneo:

- **Target Predefinito**: Se non specificato, la skill adotta **Minecraft 26.3** (`pack_format: 97.1`).
- [v1_20_2_to_1_20_4.md](references/versions/v1_20_2_to_1_20_4.md): Pack 18-22 (Overlays multi-pack, slicing 9-slice GUI sprites).
- [v1_20_5_to_1_20_6.md](references/versions/v1_20_5_to_1_20_6.md): Pack 32 (Wolf armor colorabile, atlanti particelle).
- [v1_21_0_to_1_21_1.md](references/versions/v1_21_0_to_1_21_1.md): Pack 34 (Crafter UI, Vault, Mace, canzoni Jukebox).
- [v1_21_2_to_1_21_3.md](references/versions/v1_21_2_to_1_21_3.md): Pack 42 (**Rivoluzione Equipment Assets** in `assets/<ns>/equipment/`, Bundles colorati, tint sources).
- [v1_21_4_to_1_21_5.md](references/versions/v1_21_4_to_1_21_5.md): Pack 46-55 (Winter Drop, particelle `firefly`).
- [v1_21_6_to_1_21_10.md](references/versions/v1_21_6_to_1_21_10.md): Pack 63-69.0 (**Strict JSON Mode Universale**, sprite GUI nel testo, Mannequins).
- [v1_21_11.md](references/versions/v1_21_11.md): Pack 75.0 (Zombie Nautilus asset).
- [v26_1_to_26_2.md](references/versions/v26_1_to_26_2.md): Pack 84.0-88.0 (GPU chunk rendering, Core shaders moderni, sound variants).
- [v26_3.md](references/versions/v26_3.md): Pack 97.1 (**Custom Post-Effects Shaders** per `/posteffect`, OIT shaders, `shade_direction_override`, riorganizzazione palette trims in `textures/palettes/trim/`).

---

## PARTE 3: MATRICE DI VARIAZIONE TRA LE VERSIONI

| Aspetto Tecnico | Versioni Legacy (< 1.21.2) | Versioni Intermedie (1.21.2 - 1.21.11) | Minecraft Moderno (26.1 - 26.3+) |
|---|---|---|---|
| **Texture Armature** | `textures/models/armor/` | **Equipment Assets** (`assets/<ns>/equipment/`) | Equipment Assets con `trim_overrides` |
| **Palette Trim** | `textures/trim/color_palettes/` | `textures/trim/color_palettes/` | **`textures/palettes/trim/`** e `trim_base.png` |
| **Shaders per Comandi** | Hardcoded o non controllabili | Sperimentali | **Custom Post-Effects** in `shaders/post/` per `/posteffect` |
| **Modelli Blocco (Shade)** | `"shade": true\|false` | `"shade": true\|false` | **`shade_direction_override`** (`shade` rimosso) |
| **Formato Pack in mcmeta** | Intero (es. `18`, `32`, `42`) | Intero fino a 1.21.6, **Decimale da 1.21.9 (`69.0`)** | **Decimale (`97.1` in 26.3)** |
| **Parsing JSON** | Tollerante | **Strict JSON rigoroso da 1.21.6** | Strict JSON con reporting dettagliato |

---

## PARTE 4: CICLO DI VITA E DEPRECATION DELLE VERSIONI
- I singoli file in `references/versions/` sono autonomi e disaccoppiati.
- Quando una vecchia versione (es. 1.20.2 o 1.21.0) va scemando e non è più richiesta:
  1. Si rimuove la voce corrispondente da `VERSION_INDEX.md`.
  2. Si archivia o elimina il file `.md` associato.
  3. Le Leggi Immutabili grafiche e sonore rimangono inalterate e operative.

---

## PARTE 5: WORKFLOW LINTER AUTOMATICO
Se l'utente scrive *"controlla texturepack"*, *"valida resourcepack"* o *"ottimizza asset"*:
1. Leggi `pack.mcmeta` e trova il `pack_format` della risorsa.
2. Identifica la versione bersaglio tramite `VERSION_INDEX.md`.
3. Controlla:
   - Validità del JSON (zero virgole orfane, sintassi chiusa).
   - Presenza e conformità di `pack.png` secondo la Legge 2 (Stile Modrinth Minimale).
   - File audio mono per suoni 3D ed eliminazione di formati non `.ogg`.
   - Conformità alle cartelle della versione (es. `equipment/` se >= 1.21.2, palette trim corrette se 26.3).
4. Termina segnalando fix applicati e avvisi di compatibilità.
