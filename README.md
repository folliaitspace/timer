# timer
Timer 2 min 45 sec
[README.md](https://github.com/user-attachments/files/23157943/README.md)
# TIMER (PWA)

Timer minimale per eventi, durata fissa **2:45**, design nero/giallo, installabile e **offline-ready**.

## ✨ Funzioni
- Avvio / Pausa (pulsante unico — icona `PLAY.png`)
- Reset (`RESET.png`)
- Ring giallo di avanzamento, numeri bianchi
- Logo FoLl.iA fisso in alto a destra (40px)
- Scorciatoie: **Spazio** (Avvia/Pausa), **R** (Reset)
- **PWA**: installabile su Android/iOS/Desktop, funziona offline

## 📦 Struttura
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

## ▶️ Uso locale (sviluppo)
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

## 🚀 Pubblicazione su GitHub Pages
1. Crea un repository (es. `timer-pwa`).
2. Carica **tutti i file** nella **root** del repo (non lo zip).
3. Vai su **Settings → Pages** → *Deploy from a branch* → `main` / `(root)`.
4. Apri `https://<username>.github.io/timer-pwa/`.

## 📲 Installazione come App
- **Android (Chrome/Brave/Edge):** banner *Installa app* o **⋮ → Aggiungi a schermata Home**.
- **iOS (Safari):** Condividi → **Aggiungi a Home** (poi apri dall'icona).
- **Desktop (Chrome/Edge):** icona *Installa* nella barra indirizzi.

## 🛠️ Personalizzazione
- **Durata**: in `index.html`, cambia `const DEFAULT_SECONDS = 165;` (secondi).
- **Colori**: in `:root` (CSS) modifica `--ring`, `--muted`, `--fg`, `--bg`.
- **Icone**: sostituisci `assets/PLAY.png` (usata sia per Play che Pausa) e `assets/RESET.png`.
- **Logo**: sostituisci `assets/LOGO_Follia.png` (40px fisso in alto a destra).
- **Titolo**: cambia `<title>TIMER</title>`.

## 🔄 Aggiornamenti cache (service worker)
Se dopo un deploy vedi ancora la versione vecchia:
1. Incrementa il nome della cache in `service-worker.js`, es.:
   ```js
   const CACHE_NAME = 'timer-pwa-v2';
   ```
2. Ricarica con **Hard Refresh** (Ctrl/Cmd + Shift + R).
3. In casi estremi: DevTools → **Application → Service Workers → Unregister** e ricarica.

## 🧪 Verifica rapida
- Il conteggio scende da **02:45** a **00:00**.
- Il pulsante sinistro avvia/pausa; il destro resetta.
- Con la barra spaziatrice parte/pausa; con **R** resetta.
- Funziona **offline** dopo la prima visita.

## ℹ️ Note
- L’audio non è incluso (scelta di design minimale). Aggiungibile in futuro via WebAudio.
- Su alcuni iOS, l’installazione come web app non mostra la barra indirizzi (comportamento di Safari).

---

© FoLl.iA — utilizzo interno evento.
