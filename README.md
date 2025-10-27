# timer
Timer 2 min 45 sec
[README.md](https://github.com/user-attachments/files/23157943/README.md)
# TIMER (PWA)
Timer durata fissa **2:45**, installabile e **offline-ready**.

## ✨ Funzioni
- Avvio / Pausa (pulsante unico — icona `PLAY.png`)
- Reset (`RESET.png`)
- Ring giallo di avanzamento, numeri bianchi
- Scorciatoie: **Spazio** (Avvia/Pausa), **R** (Reset)
- **PWA**: installabile su Android/iOS/Desktop, funziona offline

## Struttura
```
index.html
manifest.json
service-worker.js
assets/
  ├─ PLAY.png
  ├─ RESET.png
  └─ LOGO_Follia.png
icons/
  ├─ icon-192.png
  └─ icon-512.png
```

## Uso locale (sviluppo)
> **Nota:** il service worker non funziona da `file://`. Avvia un piccolo server locale.

Con Python 3:
```bash
cd TIMER_PWA_FINAL
python -m http.server 5173
# poi apri: http://localhost:5173/
```

Oppure con Node.js (serve / http-server a scelta):
```bash
npx http-server -p 5173 .
```

## Installazione come App
- **Android (Chrome/Brave/Edge):** banner *Installa app* o **⋮ → Aggiungi a schermata Home**.
- **iOS (Safari):** Condividi → **Aggiungi a Home** (poi apri dall'icona).
- **Desktop (Chrome/Edge):** icona *Installa* nella barra indirizzi.

## Personalizzazione
- **Durata**: in `index.html`, cambia `const DEFAULT_SECONDS = 165;` (secondi).
- **Colori**: in `:root` (CSS) modifica `--ring`, `--muted`, `--fg`, `--bg`.
- **Icone**: sostituisci `assets/PLAY.png` (usata sia per Play che Pausa) e `assets/RESET.png`.
- **Logo**: sostituisci `assets/LOGO_Follia.png` (40px fisso in alto a destra).
- **Titolo**: cambia `<title>TIMER</title>`.

## Aggiornamenti cache (service worker)
Se dopo un deploy vedi ancora la versione vecchia:
1. Incrementa il nome della cache in `service-worker.js`, es.:
   ```js
   const CACHE_NAME = 'timer-pwa-v2';
   ```
2. Ricarica con **Hard Refresh** (Ctrl/Cmd + Shift + R).
3. In casi estremi: DevTools → **Application → Service Workers → Unregister** e ricarica.

## Verifica rapida
- Il conteggio scende da **02:45** a **00:00**.
- Il pulsante sinistro avvia/pausa; il destro resetta.
- Con la barra spaziatrice parte/pausa; con **R** resetta.
- Funziona **offline** dopo la prima visita.



© FoLl.iA — 2025
