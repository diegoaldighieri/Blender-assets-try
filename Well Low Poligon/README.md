# 🪣 Well Low Poly

![Render del pozzo low poly](Renders/Well-4k.png)


 
Un pozzo in stile low poly realizzato in Blender, con tetto in tegole, rullo con manovella e una piccola base di terreno con rocce.


## 📋 Dettagli

| | |
|---|---|
| **Software** | Blender 5.2 LTS |
| **Motore di render** | Cycles |
| **Risoluzione render** | 4K (3840 × 2160) |
| **Stile** | Low poly |

## 📁 Struttura

```
Well Low Poligon/
├── Well-LowPoly.blend    # File di progetto Blender
└── Renders/
    └── Well-4k.png       # Render finale in 4K
```

## 🚀 Come usarlo

1. Clona la repository oppure scarica il file `.blend`.
2. Apri `Well-LowPoly.blend` con Blender 5.2 o versione successiva.
3. Premi **F12** per avviare il render.

Per riutilizzare il pozzo in un'altra scena: **File → Append**, seleziona `Well-LowPoly.blend` e importa la collezione `well`.

## 🛠️ Cosa ho imparato

- Separazione delle parti con **Separate → By Loose Parts**
- Materiali indipendenti per oggetto con **Make Single User → Materials**
- Illuminazione con più luci **Sun**
- Render in 4K con Cycles