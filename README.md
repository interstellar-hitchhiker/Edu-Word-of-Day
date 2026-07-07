# The Daily Lexical Biscuit

**Aka: Word of the Day!**

A vanilla JavaScript, offline-first word-of-the-day PWA with a 365-word archive, local favourites, archive search, copy-card support, and optional BBC ambience audio.

This project was refactored from the original single-file HTML prototype. The original is preserved at:

`legacy/daily-lexical-biscuit-single-file-original.html`

Live site:

`https://interstellar-hitchhiker.github.io/Edu-WoD/`

## Features

* One deterministic word of the day based on the user’s local date
* 365-word embedded archive
* Previous, next, and random word navigation
* Archive search
* Local browser favourites
* Copy-card support
* Optional ambience audio
* Offline-first PWA structure
* GitHub Pages friendly
* No login, no database, no tracking, no server

## Audio

This repository includes three local MP3 ambience files downloaded from BBC Sound Effects and placed in:

`assets/audio/bbc/`

The app reads the audio mapping from:

`assets/data/audio-library.json`

Configured audio tracks:

| App label              | Local filename                  | BBC Sound Effects lookup                                     |
| ---------------------- | ------------------------------- | ------------------------------------------------------------ |
| Song thrush birdsong   | `bbc_song-thrus_nhu0508018.mp3` | `https://sound-effects.bbcrewind.co.uk/search?q=NHU05080188` |
| Close fire / fireplace | `bbc_fire---clo_nhu0500210.mp3` | `https://sound-effects.bbcrewind.co.uk/search?q=NHU05002102` |
| Heavy rain             | `bbc_rain---hea_nhu0503213.mp3` | `https://sound-effects.bbcrewind.co.uk/search?q=NHU05032133` |

Audio behaviour:

* No audio autoplays.
* The user selects an ambience track and presses **Play ambience**.
* Changing the selected ambience refreshes the audio source.
* If audio was already playing, the newly selected ambience starts after the change.
* Audio loops quietly and uses the app’s volume slider.
* The sound files are local project files, not hotlinked BBC streams.

## BBC Sound Effects acknowledgement

This project uses selected BBC Sound Effects audio files for a free, non-commercial, educational/personal word-of-the-day web app.

BBC Sound Effects states that its archive can be used in personal/educational projects, and its FAQ says that, as a general rule, non-commercial use is free when crediting the BBC. Commercial use, including monetised, sold, paid-access, advertising-funded, or commercially sponsored use, requires licensing through Pro Sound Effects.

BBC Sound Effects:

`https://sound-effects.bbcrewind.co.uk/`

BBC Sound Effects licensing:

`https://sound-effects.bbcrewind.co.uk/licensing`

BBC Sound Effects FAQ:

`https://sound-effects.bbcrewind.co.uk/faqs`

The BBC audio files are not covered by this project’s MIT licence. They remain BBC copyright and are used under BBC Sound Effects terms.

## Run locally

Because the word archive and audio library are loaded from JSON files, run the app from a local server rather than opening `index.html` directly.

On Windows, from the extracted or cloned project folder:

```cmd
py -m http.server 8080
```

Then open:

`http://localhost:8080/`

If you are using VS Code, you can also use the Live Server extension and open `index.html` through Live Server.

## Project structure

```text
index.html
manifest.webmanifest
service-worker.js
.nojekyll
README.md
LICENSE
THIRD-PARTY-AUDIO-NOTICES.md
assets/
  css/styles.css
  js/app.js
  js/audio-player.js
  js/pwa-register.js
  js/storage.js
  js/word-engine.js
  data/words.json
  data/audio-library.json
  audio/bbc/
    bbc_song-thrus_nhu0508018.mp3
    bbc_fire---clo_nhu0500210.mp3
    bbc_rain---hea_nhu0503213.mp3
  icons/
docs/
  audio-guide.md
  deployment-guide.md
  validation-report.md
  word-data-guide.md
legacy/
  daily-lexical-biscuit-single-file-original.html
tools/
  validate-words.mjs
```

## Validate

```bash
npm run check:js
npm run validate:words
```

## Deploy on GitHub Pages

1. Keep `.nojekyll` in the repository root.
2. Keep `index.html`, `manifest.webmanifest`, and `service-worker.js` in the repository root.
3. Keep the three MP3 files in `assets/audio/bbc/`.
4. Enable GitHub Pages from the repository settings.
5. Use the repository root as the Pages source.

## Licence

The app code and original word archive are provided under the included MIT licence.

The BBC Sound Effects audio files are not MIT-licensed and are not owned by this project. They remain subject to BBC Sound Effects terms and are included here only for non-commercial educational/personal use with BBC acknowledgement.
