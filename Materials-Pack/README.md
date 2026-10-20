# Materials Pack

Libreria di materiali procedurali per Blender, pronta da usare nell'Asset Browser.
Tutti i materiali sono fatti solo con nodi: niente texture esterne, file leggero e nessun problema di licenza.

## Anteprime

| Water Orb | Stone | Ice |
| :---: | :---: | :---: |
| <img src="previews/water_orb.png" width="260" alt="Water Orb"> | <img src="previews/stone.png" width="260" alt="Stone"> | <img src="previews/ice.png" width="260" alt="Ice"> |

## Materiali

| Materiale | Come è fatto | Note |
| --- | --- | --- |
| **Water Orb** | Tre Glass BSDF (rosso, verde, blu) con IOR leggermente diversi, sommati con Add Shader per simulare la dispersione della luce. Noise Texture per il displacement. | Animato: la rotazione del Mapping è guidata da un driver. |
| **Stone** | Noise Texture e Voronoi distorto con un Mix in modalità Linear Light. Color Ramp per colore e roughness, Bump e Displacement per il rilievo. | Il Linear Light dà alle celle bordi irregolari e organici. |
| **Ice** | Principled BSDF con Transmission. Voronoi F1 per i blocchi in displacement, un secondo Voronoi in Distance to Edge per le crepe, Noise per la brina. | Le crepe usano le stesse coordinate dei blocchi, quindi combaciano con i bordi. |

## Contenuto della cartella

```
Materials-Pack/
├── Materials-Pack.blend      # tutti i materiali, marcati come asset
├── blender_assets.cats.txt   # cataloghi dell'Asset Browser
├── previews/                 # render di anteprima (uno per materiale)
└── README.md
```

## Come usarlo

1. Clona il repository o scarica la cartella `Materials-Pack`.
2. In Blender vai su **Edit → Preferences → File Paths → Asset Libraries** e clicca **+**.
3. Seleziona la cartella `Materials-Pack` e dai un nome alla libreria, ad esempio `Materials Pack`.
4. Imposta **Import Method** su **Append (Reuse Data)**, così lo stesso materiale non viene duplicato.
5. Apri l'**Asset Browser**, scegli la libreria `Materials Pack` e trascina un materiale su un oggetto.

### Requisiti

- **Blender 5.2 LTS** (creato e testato con questa versione).
- **Cycles** consigliato: la dispersione di Water Orb e il displacement reale funzionano al meglio in Cycles.
- Per il displacement: in **Material Properties → Settings → Surface → Displacement** scegli **Displacement and Bump** e aggiungi un modificatore **Subdivision Surface** all'oggetto.

## Come sono fatte le anteprime

Tutte le anteprime usano la stessa scena, così sono confrontabili tra loro:

- Cycles, 1024 × 1024 px, 512 samples, denoise attivo;
- sfera con Subdivision Surface, stessa camera per tutti i materiali;
- illuminazione con HDRI e sfondo neutro: un nodo Light Path (Is Camera Ray) mostra alla camera un colore uniforme, mentre riflessi e luce arrivano dall'HDRI.

## Crediti

- HDRI per le anteprime: [Horn-Koppe Spring](https://polyhaven.com/a/horn-koppe_spring) da Poly Haven, licenza CC0.

## Prossimi materiali

- [ ] Neve procedurale, da usare in Snow Cabin
- [ ] Palette di colori low-poly per pozzo, torre e Snow Cabin
- [ ] Node group riutilizzabili con parametri esposti
- [ ] Versioni con bake su texture per l'esportazione in Unity
