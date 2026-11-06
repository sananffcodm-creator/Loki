# Loki AI — Stage 2

Persian/English PWA task manager with local task storage, editing, filters, daily overview, analytics, JSON backup/restore, voice dictation (browser support required), speech playback, and an optional AI chat backend.

## What's included
- `index.html`: complete Stage 2 web app. Keeps the `loki_tasks` localStorage key and migrates older task records when possible.
- `manifest.webmanifest`, `sw.js`, `icons/`: installable/offline PWA shell.
- `worker/`: Cloudflare Worker API proxy. The AI provider key stays server-side.

## Deploy the website
1. Back up the current repository or download its ZIP first.
2. Upload the contents of this folder to the root of `sananffcodm-creator/Loki` on branch `main`, replacing `index.html`, `manifest.webmanifest`, and `sw.js`; upload the `icons` folder too.
3. Commit the changes and wait for the GitHub Pages deployment to finish.
4. Open `https://sananffcodm-creator.github.io/Loki/` and hard-refresh. If an old version remains, close the installed app and clear its site cache, then reopen.

## Enable real AI (optional; not needed for the task manager)
GitHub Pages is static and cannot safely store an API key. Deploy `worker/index.js` as a Cloudflare Worker (or another compatible serverless host).

Configure server-side values:
- `AI_BASE_URL`: base URL of an OpenAI-compatible chat-completions API, ending in `/v1` (the Worker appends `/chat/completions`).
- `AI_MODEL`: model identifier provided by your AI provider.
- `AI_API_KEY`: add as a secret, not a plain committed file or GitHub Pages variable.
- `ALLOWED_ORIGIN`: `https://sananffcodm-creator.github.io` (already set in `wrangler.toml`).

Then copy the Worker public URL, open Loki → Settings, paste it into Backend URL, save, and test connection. The provider must support the OpenAI-compatible `/chat/completions` interface and JSON object response format. Availability and account requirements depend on the provider and region. Do not paste API keys into Loki's browser settings.

## Important limits in Stage 2
- Tasks remain stored in each browser/device separately. Cross-device sync is not included yet.
- Voice dictation uses browser speech recognition and may not be available in every browser/language.
- When the backend is not configured, the app uses a local fallback; this is not a real AI model.
- AI-created task suggestions are only added after the user presses Add.
