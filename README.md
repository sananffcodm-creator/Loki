# Loki Pro — Stage 1

PWA foundation and enhanced task manager for the existing Loki GitHub Pages project.

## Included
- Responsive Persian/English UI
- Task create/edit/delete/complete
- Date, priority, category, and project label
- All / Today / Upcoming / Completed views
- Search and priority filter
- JSON export and restore
- PWA manifest, install prompt, app icons, service worker cache
- Loki Assist preview using local rules (not a live AI model)

## Deploy to the existing repository
1. Download and extract this ZIP.
2. Open `sananffcodm-creator/Loki` on GitHub.
3. Upload and replace `index.html` at the repository root.
4. Upload `manifest.webmanifest` and `sw.js` to the root.
5. Upload the entire `icons` folder, preserving the folder name.
6. Commit to branch `main`.
7. Wait for GitHub Actions / Pages deployment to finish.
8. Open https://sananffcodm-creator.github.io/Loki/ in Chrome on Android and choose Install app / Add to Home screen.

## Important
- Tasks are currently stored in each browser's local storage; cross-device sync is not implemented yet.
- Loki Assist is a local planning preview, not a connected generative AI model.
- A real AI connection will require a server-side proxy (for example, a Cloudflare Worker). Never put a private API key in this public repository or browser code.
- Background reminders and push notifications are a later milestone and depend on browser support and permissions.
