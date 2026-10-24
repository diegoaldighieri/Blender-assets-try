# Materials Pack

Collezione di materiali per Blender, organizzati per l'**Asset Browser** e pronti da trascinare su qualsiasi oggetto.

---

## Anteprime

<table>
  <tr>
    <td align="center"><img src="previews/dirty-glass.png" width="200"><br><b>Dirty Glass</b></td>
    <td align="center"><img src="previews/dispersion_glass.png" width="200"><br><b>Dispersion Glass</b></td>
    <td align="center"><img src="previews/gold.png" width="200"><br><b>Gold</b></td>
    <td align="center"><img src="previews/ice.png" width="200"><br><b>Ice</b></td>
  </tr>
  <tr>
    <td align="center"><img src="previews/plasma.png" width="200"><br><b>Plasma</b></td>
    <td align="center"><img src="previews/stone.png" width="200"><br><b>Stone</b></td>
    <td align="center"><img src="previews/transparent-plastic.png" width="200"><br><b>Transparent Plastic</b></td>
    <td align="center"><img src="previews/water_orb.png" width="200"><br><b>Water Orb</b></td>
  </tr>
</table>

---

## Materiali inclusi

| Materiale | Categoria | Descrizione |
|---|---|---|
| Dirty Glass | Vetro | Vetro con imperfezioni e sporco superficiale |
| Dispersion Glass | Vetro | Vetro con dispersione cromatica (effetto arcobaleno sui bordi) |
| Gold | Metallo | Oro metallico lucido |
| Ice | Trasparente | Ghiaccio semi-trasparente |
| Plasma | Emissivo | Materiale luminoso a effetto energia/plasma |
| Stone | Superficie | Pietra con dettaglio superficiale |
| Transparent Plastic | Plastica | Plastica trasparente colorata |
| Water Orb | Trasparente | Sfera d'acqua con rifrazione |

---

## Come usarlo

### Metodo 1: Asset Browser (consigliato)

1. In Blender apri **Edit → Preferences → File Paths → Asset Libraries**.
2. Clicca **+** e seleziona la cartella `Materials-Pack`.
3. Apri un editor **Asset Browser** e scegli la libreria appena aggiunta.
4. Trascina il materiale direttamente sull'oggetto nel viewport.

### Metodo 2: Append

1. **File → Append**.
2. Apri `Materials-Pack.blend` → cartella `Material`.
3. Seleziona il materiale da importare.

> **Nota:** i materiali trasparenti e rifrattivi (vetri, ghiaccio, acqua) danno il risultato migliore in **Cycles**. La dispersione del Dispersion Glass è visibile solo in Cycles.

---

## Struttura della cartella

```
Materials-Pack/
├── Materials-Pack.blend
├── README.md
└── previews/
    ├── dirty-glass.png
    ├── dispersion_glass.png
    ├── gold.png
    ├── ice.png
    ├── plasma.png
    ├── stone.png
    ├── transparent-plastic.png
    └── water_orb.png
```

---

## Prossimi passi

- [ ] Aggiungere nuovi materiali (plastica opaca, legno, metallo graffiato)
- [ ] Uniformare i nomi dei file di anteprima
- [ ] Organizzare i materiali in catalogo nell'Asset Browser per categoria
- [ ] Aggiungere una licenza d'uso