# Λεξούλες — εγκατάσταση

Static PWA: index.html + sw.js + manifest + icons. No build step, no backend.
Progress is stored in localStorage on each device.

## Deploy (any static HTTPS host)
- Firebase:  `firebase init hosting` (public dir = this folder) → `firebase deploy`
- Netlify:   drag this folder onto app.netlify.com/drop
- GitHub Pages / Render static site: push the folder, serve from root.

Open the URL once while online — the service worker caches everything,
after that it runs fully offline.

## Install on devices
- Android (Chrome): menu ⋮ → "Install app" / "Add to Home screen"
- iPhone / iPad (Safari): Share → "Add to Home Screen"
- Windows (Edge or Chrome): install icon in the address bar → "Install"

## Offline without hosting
index.html also works opened directly as a file (double-click on Windows).
On iOS a hosted URL is needed for the home-screen install.

## Voice
Uses the device's built-in text-to-speech (works offline on most devices).
If Greek isn't spoken: Android → Settings → Text-to-speech → install Greek;
iOS → Settings → Accessibility → Spoken Content → Voices → Greek;
Windows → Settings → Time & language → Speech → add Greek.

## «Πες τη λέξη» (speech recognition)
Uses the browser's Web Speech API: Chrome on Android, Edge/Chrome on Windows,
Safari on iPhone/iPad. Most devices send the audio to the browser vendor's
service, so this mode usually needs internet; all other modes stay offline.
The app asks for microphone permission the first time (HTTPS required).
The mode is hidden on browsers without speech recognition (e.g. Firefox).

## Updating
Edit index.html, then change VERSION in sw.js so devices fetch the new copy.
