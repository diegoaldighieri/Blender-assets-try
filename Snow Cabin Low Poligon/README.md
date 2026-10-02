# ❄️ Snow Cabin Low Poly

![Villaggio innevato – render finale](Renders/SnowCabin-Snow.png)

Piccolo villaggio di casette in stile low-poly immerso nella neve, con atmosfera notturna: tetti blu, luci calde dalle finestre e neve morbida che cade.

---

## 📸 Render

| Con neve | Senza neve |
|---|---|
| ![Con neve](Renders/SnowCabin-Snow.png) | ![Senza neve](Renders/SnowCabin-NoSnow.png) |

---

## 🛠️ Software e impostazioni

- **Blender** 5.2
- **Motore di render:** Cycles (GPU Compute)
- **Risoluzione:** 1600 × 1080 px
- **Sampling:** Noise Threshold 0.01, max 1024 samples
- **Denoiser:** OpenImageDenoise (Albedo + Normal)

---

## 🎨 Tecniche utilizzate

### Modellazione
- Case low-poly con struttura a graticcio (travi a vista)
- Neve sui tetti e sul terreno ammorbidita con **Shade Smooth** e **Subdivision Surface**, mantenendo le case spigolose per contrasto

### Effetti
- **Neve che cade** con un sistema di particelle: piano emettitore sopra la camera, Icosphere come fiocco, gravità ridotta e forza *Brownian* per un movimento naturale
- **Nebbia volumetrica** con un cubo e un materiale *Principled Volume*, con densità variata tramite *Noise Texture*

### Compositing (post-produzione)
Catena di nodi nel Compositor:

```
Render Layers → Bloom → Lens Distortion → Mix (Multiply) → Group Output
                         Ellipse Mask → Blur → Mix (B)
```

- **Bloom:** alone sulle finestre illuminate, con tinta calda
- **Lens Distortion:** leggera aberrazione cromatica sui bordi
- **Vignettatura:** Ellipse Mask sfumata con Blur e moltiplicata sull'immagine

---

## 📁 Struttura della cartella

```
Snow Cabin Low Poligon/
├── SnowCabin-LowPoly.blend   # File di progetto Blender
├── Renders/
│   ├── SnowCabin-Snow.png    # Render con neve
│   └── SnowCabin-NoSnow.png  # Render senza neve
└── README.md
```

---

## 🚀 Prossimi passi

- [ ] Fumo dai comignoli
- [ ] Ghiaccioli sotto le gronde
- [ ] Lanterne lungo il sentiero
- [ ] Abeti innevati attorno al villaggio
- [ ] Color grading con *Color Balance* nel Compositor
- [ ] Animazione in loop: neve che cade, finestre che tremolano, camera che ruota
