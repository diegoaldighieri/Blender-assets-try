# 🌳 Stylized Tree – Low Poly

![Stylized Tree – Low Poly](Renders/StylizedTree-LowPoly-Render.png)

Un albero low-poly in stile cartoon realizzato in **Blender 5.2 LTS**, con chioma procedurale generata tramite **Geometry Nodes** e distribuito su un terreno low-poly.

> ⚠️ **Richiede EEVEE.** Il materiale toon usa il nodo *Shader to RGB*, che non è supportato in Cycles.

---

## ✨ Caratteristiche

- **Chioma procedurale** – le foglie vengono istanziate all'interno del volume di una icosfera con i Geometry Nodes: per cambiare la forma della chioma basta modificare la mesh di base.
- **Toon shading** – materiale che reagisce alla luce con bande di colore nette, guidato dal Sun della scena.
- **Ombreggiatura morbida della chioma** – le normali delle foglie vengono prese dall'icosfera, così la chioma viene illuminata come un unico volume invece che come centinaia di piani separati.
- **Scatter sul terreno** – più alberi distribuiti su un terreno low-poly con rotazione e scala casuali.
- **Contorni Line Art** per un look da cartone animato.

---

## 🛠️ Come funziona

### Chioma (Geometry Nodes sull'Icosphere)
1. **Mesh to Volume** → **Distribute Points in Volume**: genera punti casuali all'interno della forma della chioma.
2. **Instance on Points**: posiziona l'oggetto `Leaf` su ogni punto.
3. **Sample Nearest Surface** + **Normal**: legge le normali dell'icosfera nella posizione di ogni foglia.
4. **Store Named Attribute** (`normals`, dominio Instance): salva quelle normali per lo shader.
5. **Random Rotation** / **Random Value**: variano orientamento e scala delle foglie.

### Materiale toon
`Diffuse BSDF → Shader to RGB → Map Range → Color Ramp (Constant) → Material Output`

- Il materiale **Leaf** legge le normali salvate tramite un nodo **Attribute** (modalità *Instancer*, `normals`) collegato all'ingresso *Normal* del Diffuse.
- Il materiale del **tronco** usa le normali della propria mesh (senza nodo Attribute), così ogni faccia low-poly riceve la luce in modo diverso.

### Scatter sul terreno
Il terreno usa il modificatore **Scatter on Surface**:
- **Instance Type:** Collection (`Tree_sources` → Trunk + Icosphere)
- **Distribution Mask:** vertex group `Scatter_Top`, così gli alberi compaiono solo sulle facce superiori
- **Align Rotation:** disattivato, così gli alberi crescono sempre dritti
- **Randomize:** rotazione Z 180°, leggera inclinazione X/Y (5°), scala uniforme ±0.2

---

## 📁 Organizzazione della scena

| Collection | Contenuto |
|---|---|
| `Tree_sources` | Trunk + Icosphere (l'albero che viene distribuito, nascosto dalla scena) |
| `Tree_Parts` | Oggetto `Leaf` usato dai Geometry Nodes (nascosto) |
| `Terrain` | Mesh del terreno con il modificatore Scatter on Surface |
| `Camera and light` | Camera, Sun |

> L'oggetto `Leaf` deve restare nel file anche se nascosto: i Geometry Nodes della chioma lo richiamano tramite un nodo *Object Info*.

---

## 📂 Struttura della cartella

```
StylizedTree/
├── README.md
├── StylizedTree-LowPoly.blend
└── Renders/
    └── StylizedTree-LowPoly-Render.png
```
