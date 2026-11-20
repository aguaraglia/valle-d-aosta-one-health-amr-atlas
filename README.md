# Valle d'Aosta One Health AMR Atlas

Edizione regionale `vda_amr_atlas`, pubblicata da Codex Vitae ETS sulla stessa
base delle edizioni Liguria e Piemonte.

Sito pubblico: <https://aguaraglia.github.io/valle-d-aosta-one-health-amr-atlas/>

## Stato

L'evidenza pubblicata per la Valle d'Aosta è molto scarsa. Questa è un'edizione
piccola: solo 5 studi inclusi, tutti a scala regionale. La mappa mostra il
solo contorno regionale e nessuna struttura, comune o provincia.

Letteratura scientifica del 20 novembre 2026: 5 studi con collegamento
territoriale esplicito alla Valle d'Aosta, in sei layer (AMR umana,
veterinaria, alimentare, ambientale, fauna selvatica, studi a scala regionale).
Il contorno regionale ha 1 elemento e 5 studi. I layer umano, veterinario,
alimentare, ambientale e della fauna selvatica sono vuoti: l'area senza
segnaposto è nessuna evidenza pubblicata, non resistenza zero. Ogni popup cita
lo studio e il DOI (o il record PubMed se il DOI non è assegnato) e ricorda
che il segnaposto è il luogo dello studio, non una prevalenza.

Fonti istituzionali pubbliche: AR-ISS 2024 (CC BY 4.0, copertura 100%, rete
regionale propria) e AIFA Open Data 2024, antibatterici J01 (CC BY 4.0).
Scheda ambientale ARPA Valle d'Aosta, «Lo studio dell'antimicrobico resistenza
in Valle d'Aosta», Ecoscienza 3/2025, pp. 24-25 (CC BY-NC-SA 4.0): evidenza
senza segnaposto, perché i due depuratori non sono nominati, con attribuzione
e nota «condividi allo stesso modo». Confini ISTAT 2026 (74 comuni, 1
provincia, regione), letti in UTF-8. Nessuna struttura nominata e nessuna
query Nominatim. Azienda USL della Valle d'Aosta, Regione autonoma Valle
d'Aosta e il PDF OsMed sono esclusi: vedi `metadata/EXCLUDED_SOURCES.md`.

Il conteggio in homepage e in pubblicazioni legge
`public/data/literature-catalog.json` (5).

## Pagine

Sorgente su `main`. Il sito statico è pubblicato dal branch `gh-pages`
(GitHub Pages, cartella `/`). Nessun file `CNAME`. Analitica: GoatCounter
`https://atlanteamr.goatcounter.com/count`, come le edizioni Liguria e Piemonte.

## Build locale

```bash
python3 -m http.server 8000
```

Aprire `http://localhost:8000/`.

Per rigenerare i dati pubblici servono gli input in `raw/` e, per i confini,
l'archivio ISTAT indicato in `metadata/SNAPSHOTS.tsv`:

```bash
pip install -r requirements-geodata.txt
python3 scripts/build_istat_geography.py --source-root <Limiti01012026_g> --output-root public/geography
python3 scripts/build_literature_catalog.py
python3 scripts/build_study_evidence_layers.py
```

## Directory

- `public/`: dati e asset approvati per il sito;
- `metadata/`: fonti, snapshot, ambito pubblico e fonti escluse;
- `raw/`: curatela ed esummary PubMed (nessuna risposta Nominatim);
- `scripts/`: ricostruzione del catalogo e dei layer;
- `private/`: nessun dato riservato in questa edizione.
