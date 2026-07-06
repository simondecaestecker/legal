# legal — repo doc

Static site hosting Privacy Policy / EULA (CGU) pages for all Simon's apps. Pure HTML/CSS/vanilla JS, no build step, no framework. Deployed as-is (check hosting via repo remote/README if unsure — currently no explicit deploy config in repo).

## Structure

```
index.html              # root landing page, lists every app with links to its legal docs
<app-slug>/
  index.html            # (optional) small landing page for the app's own legal section
  privacy.html          # Privacy Policy (or index.html doubles as privacy — see existing apps)
  eula.html             # EULA / CGU
```

Existing apps: `studio-pdf/`, `video-toolbox/`, `grilles-calcul/`, `roxtrain/`. Naming is not 100% consistent historically (e.g. `studio-pdf/index.html` IS the privacy page, `grilles-calcul` uses `cgu.html` instead of `eula.html`). For **new apps**, follow the `roxtrain/` pattern: separate `index.html` (landing), `privacy.html`, `eula.html`.

## Page pattern (copy from `roxtrain/` as template)

Each privacy.html / eula.html:
- Self-contained: inline `<style>`, no external assets/fonts/CDN.
- Bilingual FR/EN via two `<div class="lang-version">` blocks toggled by a JS `toggleLang()` button (no page reload, no i18n lib).
- Dark mode via `@media (prefers-color-scheme: dark)`.
- Card-style container (`max-width: 800px`, white/dark bg, rounded corners, shadow) — matches root `index.html` visual style.
- Contact email convention: `<appslug>@simondecaestecker.com` (no dots, all lowercase, matches app folder slug).
- `<div class="app-name">`/`app-desc` cards on the root `index.html` link out to `<slug>/eula.html` and `<slug>/privacy.html`.

## Adding a new app: checklist

1. `mkdir <app-slug>` (slug = kebab-case, matches the app's own repo/dir name where possible).
2. Copy `roxtrain/index.html`, `roxtrain/privacy.html`, `roxtrain/eula.html` into the new folder as templates.
3. Read the target app's `package.json` / `app.json` / `README.md` in its own repo (e.g. `../<app-slug>`) to get: what it does, whether it stores data locally vs. remotely (backend/API?), what third-party SDKs it uses (analytics, ads, payments/RevenueCat, crash reporting, push notifications, health data, etc.) — each of these needs its own clause if present.
4. Update privacy.html: data collection section must accurately reflect real data flows (local-only SQLite/AsyncStorage vs. actual server calls, any analytics/ads SDKs, any accounts/auth).
5. Update eula.html: standard clauses (license grant, restrictions, IP, disclaimer, liability, termination) + any domain-specific disclaimer (e.g. health/fitness apps need a "not medical advice" clause, apps handling money need explicit payment-processor mention).
6. Set both dates to today, subject line/title to the app's real name, contact email to `<slug>@simondecaestecker.com`.
7. Add app card to root `index.html`: new `.app-card` block + FR/EN entries in the `translations` object (`appNameKey`, `appNameDescKey`).
8. Sanity check: open root `index.html` and new pages in a browser, click through both languages, check dark mode.

## Notes
- No package.json / build tooling in this repo — just edit HTML directly.
- Keep new apps consistent (index+privacy+eula three-file layout) even though older folders vary — don't retrofit old ones unless asked.
