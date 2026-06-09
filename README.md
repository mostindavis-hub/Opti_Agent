# Optimizely Agent Finder

Find the right Optimizely agent for a customer conversation — analyze a sales/discovery call and get a recommended agent workflow. Everything runs **locally in the browser**: audio is transcribed on-device, and nothing is uploaded.

The entire app ships as a single self-contained `index.html` — no build step, no server, no dependencies to install.

## Use it

Open the published page (see **Deploy** below), then pick one of three ways to give it a conversation:

- **Record live** — capture the call (and system/tab audio) and transcribe it on-device.
- **Upload audio** — drop in an existing recording to transcribe.
- **Paste transcript** — paste a transcript from your meeting tool and analyze it directly.

> **First run downloads the speech model (~80 MB).** This happens once, from a public CDN, then it's cached and works offline. Do this once on an open network before any live test.

### If live recording can't transcribe
If on-device transcription is unavailable or fails, the app won't lose your take. It keeps the recording and drops you into **Paste transcript** — carrying over any text it managed to capture — so you can paste a transcript, retry transcription, or download the audio.

## Deploy (GitHub Pages)

1. Create a new repository and add `index.html` to it.
2. **Settings → Pages → Build and deployment**: Source = **Deploy from a branch**, Branch = **`main` / `/ (root)`**, then **Save**.
3. After ~1 minute your app is live at `https://<your-username>.github.io/<repo-name>/`.

Serving over `https://` matters: opening the file directly from disk (`file://`) blocks the background worker that loads the transcription model, so live recording won't work that way.

## Requirements

- A recent **Chrome, Edge, or Safari**. On-device transcription uses WebAssembly/WebGPU via the browser.
- An **open network** for the one-time model download (corporate/conference wifi sometimes blocks the CDN).
- For best results on a live call, use a browser that lets you share **tab or system audio** when recording.

## Privacy

Audio and transcripts are processed entirely in your browser. No audio, transcript, or analysis is sent to a server.
