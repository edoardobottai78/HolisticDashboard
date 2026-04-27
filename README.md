# Holistic Dashboard

Dashboard mensile integrata — dati fisici, mentali, nutrizionali e di performance.

## Stack
- Single-file PWA (`index.html`)
- `data.json` come fonte dati (aggiornato mensilmente)
- Deploy: Vercel + GitHub

## Struttura repo
```
HolisticDashboard/
├── index.html      # App completa
├── data.json       # Dati del mese corrente
├── vercel.json     # Config Vercel
└── README.md
```

## Come aggiornare i dati ogni mese

A fine mese, dopo aver salvato il Monthly Holistic Report su Notion, apri una nuova chat con Claude e scrivi:

```
AGGIORNA_DASHBOARD
```

Claude leggerà il Monthly Holistic Report da Notion, genererà il nuovo `data.json` e te lo fornirà da sostituire nel repo.

**Procedura di aggiornamento:**
1. Ricevi il nuovo `data.json` da Claude
2. Vai su github.com → repository `HolisticDashboard`
3. Clicca su `data.json` → matita (edit) → incolla il nuovo contenuto → commit
4. Vercel fa il deploy automaticamente in ~30 secondi

## Campi data.json

Il file contiene tutti i 44 campi del Monthly Holistic Report più:
- `mood_tipo[]` — array di 28 valori: "pos", "neu", "dif"
- `parole_frequenti[]` — array di oggetti `{parola, tipo, peso}`
- `piani_distribuzione[]` — array piani alimentari con pct e giorni
- `protocollo_sessioni[]` — distribuzione esercizi del protocollo
- Testi qualitativi: `temi_mese`, `riflessioni_protocollo`, `azioni_prioritarie`

I campi `null` (es. SPORT_DATA non ancora popolato) vengono mostrati come `—` nella dashboard senza errori.

## URL
Dopo il deploy sarà disponibile su: `https://[nome-progetto].vercel.app`
