<!--
  Purpose: Guidance for AI coding agents (small, focused, actionable).
  Keep this file short (~20-50 lines) and specific to this repo.
-->

# Guidance for AI coding agents — Souel

Summary
- Small single-file static app: `index.html` (React UMD + Babel standalone + Tailwind CDN).
- This is a mobile-friendly travel itinerary viewer — no build step, no tests, and no server required for development.

What to edit / where to look
- Primary application & data live in `index.html`.
  - Main dataset: `ITINERARY_DATA` (array of day objects). Update here to change the app content.
  - UI helpers: `getTypeColor`, `getTypeEmoji`, `openNaverMap`, `openGoogleSearch` live in the same file — keep edits local and minimal.

Data shape — event object (example)
```js
{
  id: 101, time: '10:00', type: 'transport', title: '抵達仁川機場', koreanName: '인천국제공항',
  desc: '桃園T2 -> 仁川T1 (CI160)。辦理入境手續。',
  meta: { from: '桃園T2', to: '仁川T1' }, tips: ['已預約 CI160 航班']
}
```

Important patterns & constraints
- App uses in-browser JSX compilation (Babel standalone). This is optimized for prototypes — large-scale changes should introduce a build system (Vite/webpack) but keep current format for quick edits.
- Icons use Emoji (Icon component) rather than icon libraries — keep this convention for lightweight cross-platform visuals.
- Styling is Tailwind via CDN. Use utility classes in `index.html` to match the existing style.

Run / test locally
- Quick way: open `index.html` in a browser (double-click) or run a lightweight static server to avoid file-protocol pitfalls:
  - Python 3: `python3 -m http.server 8000` then open `http://localhost:8000`.
  - Node (optional): `npx serve` or `npx http-server`.

Debugging tips
- Use devtools console and Elements inspector. All logic is inline in `index.html` so edits are fast.
- When adding new events/days: ensure unique numeric `id` values and consistent `type` strings (food, cafe, transport, shopping, stay, bar, attraction).

When to create a PR
- Small content or UI tweaks: single-file PR with short explanation.
- Structural changes (introducing a build chain, splitting files, adding tests): include migration notes and update `README.md`.

If anything is unclear or missing (e.g. more runtime commands, CI, or external services), ask for clarification before making large-scale changes.
