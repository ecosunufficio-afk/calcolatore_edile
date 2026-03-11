# 🏗️ Calcolatore Edile — Guida rapida

## Come usare

1. **Apri** il file `calcolatore-edile.html` con qualsiasi browser (Chrome, Firefox, Edge, Safari)
2. Nessuna installazione richiesta — funziona completamente offline

---

## Struttura file

```
calcolatore-edile/
├── calcolatore-edile.html   ← App principale (apri questo)
├── database.json            ← Backup/import dei preventivi
└── README.md                ← Questa guida
```

---

## Funzionalità

### Calcolo materiali
- Scegli la **macro-categoria** dal menu laterale
- Seleziona la **lavorazione** (es. Intonaci) poi il **materiale**
- Inserisci la **superficie/volume**, scegli il **formato confezione**
- Il calcolatore applica automaticamente: `sacchi = ceil(superficie × resa × (1+margine%) / kg_sacco)`

### Modifica voci
- Ogni voce ha il pulsante **✏️ Modifica**
- Puoi cambiare: nome prodotto, resa, confezioni (label, kg, prezzo), quantità, margine
- Il calcolo si aggiorna in tempo reale

### Salvataggio
- Premi **💾 Salva progetto** nella barra laterale
- I preventivi vengono salvati nel browser (localStorage)
- Per **backup permanente**: vai in Storico → "Esporta DB (JSON)" → salva il file `database.json`

### Importazione
- In Storico → "Importa DB" → seleziona un file `database.json` precedentemente salvato
- Utile per trasferire i dati su un altro computer

### Esportazioni
- **🖨️ PDF** — apre una finestra di stampa ottimizzata (abilita i popup del browser)
- **📊 Excel** — esporta `.xls` compatibile con Microsoft Excel e LibreOffice Calc
- **📄 CSV** — file testo separato da punto e virgola, compatibile con qualsiasi foglio di calcolo

---

## Note sui prezzi
I prezzi preimpostati sono **valori medi indicativi** (€ per confezione).
Aggiornali sempre dalla finestra **✏️ Modifica** in base ai prezzi reali del tuo fornitore.

---

## Formula di calcolo
```
fabbisogno = superficie × resa × (1 + margine / 100)
n_confezioni = ceil(fabbisogno / kg_per_confezione)
costo = n_confezioni × prezzo_confezione
```

**Esempio:** 20 m² · resa 20 kg/m² · +10% margine · sacco 25 kg a €4
→ fabbisogno = 20 × 20 × 1.10 = 440 kg
→ sacchi = ceil(440 / 25) = **18 sacchi**
→ costo = 18 × €4 = **€72**
