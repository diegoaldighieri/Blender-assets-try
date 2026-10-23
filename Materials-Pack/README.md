# Materials Pack

Una raccolta di materiali procedurali per Blender, pronti da usare dall'**Asset Browser**. Ogni materiale è costruito interamente con i nodi, senza texture esterne, quindi funziona a qualsiasi risoluzione e si può modificare liberamente.

## Anteprima

| | | |
|:---:|:---:|:---:|
| ![Dirty Glass](previews/dirty-glass.png) | ![Dispersion Glass](previews/dispersion_glass.png) | ![Gold](previews/gold.png) |
| **Dirty Glass** | **Dispersion Glass** | **Gold** |
| ![Ice](previews/ice.png) | ![Plasma](previews/plasma.png) | ![Stone](previews/stone.png) |
| **Ice** | **Plasma** | **Stone** |
| ![Water Orb](previews/water_orb.png) | | |
| **Water Orb** | | |

## Requisiti

- **Blender 5.2 LTS** o successivo
- **Cycles** consigliato per i materiali trasparenti (Dirty Glass, Dispersion Glass, Ice, Water Orb). In EEVEE il vetro richiede il Raytracing attivo e può comunque apparire diverso.

## Materiali inclusi

### Dirty Glass
Vetro trasparente con aloni di sporco e opacità irregolare.
- Un **Noise Texture** passa per una **Color Ramp** che controlla la *Roughness* del Glass BSDF: le zone nere restano trasparenti, quelle grigie diventano satinate.
- Una seconda Color Ramp pilota un nodo **Bump** per le micro-imperfezioni della superficie.
- Un **Light Path** (*Is Shadow Ray*) mescola un Transparent BSDF per ombre più chiare.
- Un **Layer Weight** (*Fresnel*) aggiunge un'Emission leggera sui bordi.

**Da regolare:** la posizione delle due stop della Color Ramp della roughness decide quanto sporco c'è. Tieni lo stop di destra grigio, non bianco, per evitare macchie completamente opache.

### Dispersion Glass
Vetro con dispersione cromatica: la luce rifratta si separa nei colori dell'arcobaleno sui bordi.

### Gold
Metallo dorato.

### Ice
Ghiaccio semi-trasparente.

### Plasma
Sfera di energia viola, ispirata a un reattore al plasma.
- Una **Wave Texture** (Bands, Sine) alimenta sia il **Displacement** sia lo shader, creando il rilievo ondulato.
- Un **Fresnel** collegato a una **Color Ramp** dal nero al viola colora l'**Emission** in base all'angolo della superficie: è ciò che rende visibili i dettagli del rilievo.
- Un **Layer Weight** (*Facing*) mescola emissione e pattern tramite un Mix Shader.

**Da regolare:** la *Strength* dell'Emission per l'intensità del bagliore, e il *Phase Offset* della Wave Texture per animarlo (ad esempio con il driver `#frame*0.05`).

**Nota:** l'impostazione del materiale deve essere *Displacement and Bump* (Material Properties → Settings). Per il bagliore usa il nodo **Glare** nel Compositor.

### Stone
Pietra.

### Water Orb
Sfera d'acqua trasparente.

## Installazione

1. Scarica o clona questo repository.
2. In Blender apri **Edit → Preferences → File Paths → Asset Libraries**.
3. Clicca **+** e seleziona la cartella `Materials-Pack`.
4. Apri un editor **Asset Browser** e scegli la libreria appena aggiunta dal menu in alto a sinistra.
5. Trascina un materiale direttamente su un oggetto nel viewport.

> Il file `blender_assets.cats.txt` contiene le categorie dell'Asset Browser: tienilo nella stessa cartella del file `.blend`.

## Consigli per la scena

I materiali trasparenti mostrano ciò che hanno intorno. Se dietro l'oggetto c'è solo nero, il vetro sembrerà nero o cromato.

- Usa un **fondale curvo** grigio scuro dietro l'oggetto, illuminato da un'Area Light.
- Aggiungi due **Area Light** strette e alte ai lati per disegnare i riflessi sui bordi.
- Se usi un HDRI per l'illuminazione ma vuoi uno sfondo scuro, nel World usa un **Mix Shader** con Factor = *Maximum* tra **Is Camera Ray** e **Is Transmission Ray**. Così lo sfondo scuro si vede sia direttamente sia attraverso il vetro.
- Per oggetti in vetro, modella pareti e fondo con uno **spessore reale** (Inset + Extrude) e smussa i bordi con un **Bevel**.

## Struttura della cartella

```
Materials-Pack/
├── Materials-Pack.blend
├── blender_assets.cats.txt
├── previews/
│   ├── dirty-glass.png
│   ├── dispersion_glass.png
│   ├── gold.png
│   ├── ice.png
│   ├── plasma.png
│   ├── stone.png
│   └── water_orb.png
└── README.md
```

## Prossimi passi

- [ ] Completare la descrizione dei nodi per Dispersion Glass, Gold, Ice, Stone e Water Orb
- [ ] Uniformare i nomi delle anteprime (trattino o underscore)
- [ ] Aggiungere un'anteprima animata del Plasma (GIF o video in loop)
- [ ] Creare una scena "studio" di riferimento con fondale e luci, inclusa nel pack
- [ ] Definire la licenza d'uso