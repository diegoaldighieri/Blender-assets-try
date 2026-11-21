# ☕ Coffee & Cookies

Scena stilizzata di una pausa caffè: una tazzina di espresso sul piattino, un cookie con gocce di cioccolato, due meringhe e bastoncini di cannella. Progetto incentrato su **materiali procedurali** e **illuminazione a tre punti** in Cycles.

![Render finale](Renders/Coffee-Cookies.png)

---

## 📋 Dettagli

| | |
|---|---|
| **Software** | Blender 5.2.4 LTS |
| **Motore di render** | Cycles |
| **Color Management** | AgX |
| **Stile** | Stilizzato, forme morbide e colori caldi su sfondo freddo |

---

## 🛠️ Workflow

### 1. Modellazione

- **Piatto**: Circle con riempimento N-gon → estrusione e scala per creare la parete inclinata e la tesa piatta → Solidify per lo spessore + Subdivision Surface e Shade Smooth.
- **Cookie**: Subdivision Surface + modificatore **Displace** con texture *Clouds* per rendere i bordi irregolari.
- **Gocce di cioccolato**: oggetti low-poly separati, parzialmente affondati nell'impasto e **imparentati al cookie** (`Ctrl+P → Object (Keep Transform)`), così si spostano insieme.
- **Tazza, meringhe e cannella**: modellazione a bassa risoluzione + Subdivision Surface per un look morbido.

### 2. Materiali

Tutti i materiali usano il **Principled BSDF**. La differenza di lucidità (Roughness) tra i materiali è ciò che li rende riconoscibili.

| Oggetto | Base Color | Roughness |
|---|---|---|
| Tazza e piatto | `#F0EBE4` | 0.1–0.15 |
| Caffè | `#3A2214` | 0.1 |
| Gocce di cioccolato | `#2E1A12` | 0.3 |
| Cookie (centro → bordi) | `#C68A4E` → `#8A4F2A` | 0.8 |
| Meringhe | `#F3E6D3` | 0.6–0.8 |
| Cannella | `#8B4A2B` | 0.7–0.8 |

#### Shader procedurale del cookie

```
Colore (bordi scuri, centro chiaro)
Texture Coordinate (Generated) → Mapping (Loc X/Y -0.5, Scale Z 0) → Gradient Texture (Spherical) → Color Ramp

Macchie irregolari
Color Ramp × Noise Texture (Scale 5) → Mix Color (Multiply, Factor 0.3) → Base Color

Grana della superficie
Noise Texture (Scale 40, Detail 8) → Bump (Strength 0.3) → Normal
```

### 3. Illuminazione

Schema a **tre punti** con aree luminose. I colori sono impostati in gradi Kelvin (Temperature) con Tint bianco, per avere tinte naturali e controllate.

| Luce | Ruolo | Temperatura | Power | Size | Note |
|---|---|---|---|---|---|
| **Key** | Luce principale | 5000 K | 1500 W | 0.75 m | Piccola per ombre più definite |
| **Fill** | Riempimento ombre | 8000 K | 500 W | 2.89 m | Fredda, lega gli oggetti allo sfondo azzurro |
| **Rim** | Controluce | 3000 K | 1250 W | 2.89 m | Dietro gli oggetti, constraint *Track To* sulla tazza |

### 4. Render

- Cycles con denoise
- View Transform: AgX

---

## 📁 Struttura della cartella

```
Coffee-Cookies/
├── Coffee-Cookies.blend
├── Renders/
│   └── Coffee-Cookies.png
└── README.md
```

---

## 💡 Cosa ho imparato

- **Parenting**: l'ordine di selezione conta (il genitore va selezionato per ultimo). Se un oggetto è già figlio di un altro, invertire la relazione genera l'errore *Loop in parents* → si risolve con `Alt+P → Clear and Keep Transformation`.
- **Outliner**: `Ctrl+clic` aggiunge alla selezione, `Shift+clic` seleziona un intervallo.
- **Cycles vs EEVEE**: in Cycles la rifrazione del vetro è sempre fisicamente corretta. *Screen Space Refraction* (oggi *Raytraced Transmission*) esiste solo in EEVEE.
- **Luci colorate**: con *Temperature* attiva il campo Color diventa *Tint* e si moltiplica con la temperatura. Più luci colorate con la stessa potenza tingono tutta la scena: la luce principale va tenuta neutra e il colore messo su fill e rim.
- **Diagnosi rapida**: se i colori del render sembrano sbagliati, passare in *Material Preview* aiuta a capire se il problema sono i materiali o le luci.
- **Rim light**: va posizionata dietro gli oggetti, lontana e poco più in alto, puntata con *Track To*.
- **Scorciatoie utili**: `Ctrl+Shift+Z` (ripeti), `Ctrl+Alt+Z` (cronologia annullamenti), `Shift+R` (ripeti ultima azione).

---

## ✅ Prossimi passi

- [ ] Morso nel cookie (Boolean) e briciole sul piatto
- [ ] Vapore dal caffè
- [ ] Zollette di zucchero o cucchiaino nella zona libera del piatto
- [ ] Crema dell'espresso lungo il bordo del caffè
- [ ] Venature della cannella con Wave Texture
- [ ] Depth of Field con fuoco sulla tazza
- [ ] Confronto tra stili di luce colorata (Teal & Orange, Pastello, Neon)
- [ ] Render **clay** e **wireframe** da aggiungere al README

<!--
Galleria da completare quando i render sono pronti:

| Clay | Wireframe |
|---|---|
| ![Clay](Renders/coffee-cookies-clay.png) | ![Wireframe](Renders/coffee-cookies-wireframe.png) |
-->
