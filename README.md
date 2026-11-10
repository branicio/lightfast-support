# Lightfast — Support

Support, legal and group-fast pages for **Lightfast: Daniel Fast**
(`com.branicio.lightfast` on both platforms), a Christian spiritual-fasting
companion for iPhone and Android. Static HTML/CSS/JS, served by GitHub Pages at
<https://branicio.github.io/lightfast-support/>. No build step, no JavaScript
libraries, no cookies, analytics or trackers, and no external resources: the
fonts (Spectral + Figtree) are self-hosted in `fonts/`.

**https://branicio.github.io/lightfast-support/**

## Live URLs — and why the filenames are frozen

Served by GitHub Pages from the `main` branch root (`source: main /`): anything pushed to root
is live within a minute or two. All of these returned `200` on 2026-11-09 and must keep returning
`200`:

| URL | Resolves to | Linked from |
|---|---|---|
| https://branicio.github.io/lightfast-support/ | `index.html` | both apps (Settings › Help and support), App Store and Google Play support URL |
| https://branicio.github.io/lightfast-support/privacy | `privacy.html` | — |
| https://branicio.github.io/lightfast-support/privacy.html | `privacy.html` | both apps (Settings, paywall, onboarding's Terms step), App Store Connect privacy URL, Google Play, every store description |
| https://branicio.github.io/lightfast-support/terms | `terms.html` | — |
| https://branicio.github.io/lightfast-support/terms.html | `terms.html` | both apps (Settings, paywall, onboarding's Terms step), every store description; the App Store custom EULA is built from it |
| https://branicio.github.io/lightfast-support/impressum | `impressum.html` | — |
| https://branicio.github.io/lightfast-support/impressum.html | `impressum.html` | every page's footer (Legal notice) |
| https://branicio.github.io/lightfast-support/join/ | `join/index.html` | group-fast invitations from both apps (`/join/?j=<journey>&s=<yyyy-MM-dd>&n=<name>`) |
| https://branicio.github.io/lightfast-support/privacy-android.html | redirect to `privacy.html` | older Android builds and the first Play listing |
| https://branicio.github.io/lightfast-support/terms-android.html | redirect to `terms.html` | older Android builds and the first Play listing |

The apps open each legal page with the reader's language as a fragment: `#portugues`, `#espanol`,
`#francais`, `#italiano`, `#deutsch` (English has none), e.g.
https://branicio.github.io/lightfast-support/terms.html#deutsch.

GitHub Pages resolves the extensionless forms (`/privacy`, `/terms`, `/impressum`) to the matching
`.html` file by itself; there is no redirect rule to configure, and it works only while the files
keep these names. **Don't rename `index.html`, `privacy.html`, `terms.html`, `impressum.html` or
`join/index.html`**: the URLs are compiled into shipped app builds (iOS `Legal` in
`PaywallView.swift`, Android `Links`), registered in App Store Connect and Google Play, and printed
in invitations people have already shared. A rename needs new app builds and store updates first.

Paulo's name and postal address appear only in `impressum.html` (German law, § 5 DDG); every other
page gives the email braniapps@gmail.com only (2026-11-09).

| File | What it is |
|---|---|
| `index.html` | Support page: features, the 11 journeys, food guide and scanner, group fasts, Free vs Plus, FAQ, contact |
| `privacy.html` | Privacy Policy for both apps (effective November 3, 2026) |
| `terms.html` | Terms of Use / EULA for both apps (effective November 9, 2026; both apps ask people to accept this version) |
| `privacy-android.html`, `terms-android.html` | Redirects to `privacy.html` / `terms.html` that keep the language fragment (older Android builds and the first Play listing linked here) |
| `impressum.html` | Impressum / legal notice (§ 5 DDG): one static page, German, English and French in full plus a line per other language; text from `Marketing/legal-eu/eu_legal_texts.py`, linked from every footer |
| `join/index.html` | Group-fast invitation landing page (`/join/?j=<journey>&s=<yyyy-MM-dd>&n=<group name>`) |
| `404.html` | Not-found page (GitHub Pages serves it for any missing path) |
| `styles.css`, `site.js`, `app-icon.png` | Shared styles, language switcher, 512 px app icon |
| `fonts/` | Self-hosted Spectral + Figtree (woff2, latin + latin-ext), `fonts.css` and the OFL `LICENSES.txt`, made by `Marketing/legal-eu/selfhost_fonts.py` so no visitor request goes to Google |

## Languages

Every page is in English, Português (Brasil), Español (neutral Latin American),
Français, Italiano and Deutsch, with the same mechanism as the Nistikon support site: each page
carries `[data-lang]` blocks for all six languages, shared chrome uses
`data-i18n-*` / `data-i18n-aria-*` attributes, and `site.js` shows one language,
chosen by the `#portugues` / `#espanol` / `#francais` / `#italiano` / `#deutsch` URL fragment, then the
EN · PT · ES · FR · IT · DE tabs (remembered in `localStorage`), then the browser
language (any `de*` locale opens German). Without JavaScript the six languages render stacked, so legal text
is never hidden. Both apps' legal links append the fragment for the in-app language
(iOS `Legal.privacy/terms` in `PaywallView.swift`, Android `Links` in
`LightfastRoot.kt`).

## One site for iPhone and Android

The pages serve both apps equally. Text is written for a phone owner first
("your phone", "the app"); where the platforms really differ, the difference is
stated as a pair — **On iPhone:** … / **On Android:** … (pt *No iPhone / No
Android*, es *En iPhone / En Android*, fr *Sur iPhone / Sur Android*, it *Su iPhone / Su Android*,
de *Auf dem iPhone / Auf Android*) — with the
same depth on each side and iPhone always first: backups and new phones,
Live Activity vs the ongoing fast notification, widgets, the camera and text
recognition (Vision vs Tesseract), purchases, managing, restoring, Family
Sharing, refunds and the store terms (Apple's standard EULA vs Google Play).
Each platform keeps its own vocabulary (Apple Account, Settings › [your name] ›
Subscriptions; Google Account, Play Store › Payments & subscriptions; in German
Apple Account, Einstellungen › [dein Name] › Abonnements, Familienfreigabe, „Mitteilungen“;
Google-Konto, Play Store › Zahlungen und Abos › Abos, „Benachrichtigungen“). Headings
in pt/es/fr/it use sentence case (German capitalises nouns as usual), and every page's browser-tab title follows the
chosen language (`data-i18n-*` on `<title>`; the join page retitles itself).

French and Italian address the reader as *tu* and German as *du*, matching the app's content guide;
German follows the binding glossary (`docs/superpowers/plans/2026-11-03-german-glossary.md`:
„…“ quotes, the spaced en dash, *Weg/Wege* for journey) and quotes only the Lutherbibel 1912.
The pt/es/fr/it/de names of in-app buttons, tabs and screens (e.g. es *jornada*,
*Ora como Daniel*, *Ayuno digital*; fr *Aliments*; de *Wege*, *Essen*, *Beten wie Daniel*) follow the app's String
Catalog (`content/ui/<lang>.json`); keep them in step when the catalog changes.

## Group-fast links

Both apps share `https://branicio.github.io/lightfast-support/join/?j=daniel-21&s=2027-01-04&n=Grace%20Church`
(iOS `DeepLink.swift`, Android `DeepLink.kt`), and either app opens a link made
by the other. `join/index.html` validates the link with the same rules as
the apps (known journey id, real date within 400 days, group name cleaned to
letters/digits/basic punctuation, max 60 characters), shows the journey title
and start date in the visitor's language, writes the group name with
`textContent` only, and rebuilds `lightfast://join?j=…&s=…&n=…` with
`encodeURIComponent`. Anything invalid shows "This invitation link looks
incomplete". If a journey is added to the app, add its id and titles to
`JOURNEYS` in `join/index.html`.

## Publish (GitHub Pages)

1. Create the public repository `branicio/lightfast-support` and push the
   *contents* of this folder to the root of its `main` branch.
2. On GitHub: **Settings › Pages › Build and deployment › Source: Deploy from a
   branch**, branch `main`, folder `/ (root)`, Save.
3. After a minute, check <https://branicio.github.io/lightfast-support/>,
   `privacy.html#portugues`, `terms.html#francais`, `index.html#italiano`, `index.html#deutsch`, `impressum.html#deutsch`, a missing path (404 page)
   and `join/?j=daniel-21&s=2027-01-04&n=Grace%20Church`.

`404.html` uses absolute `/lightfast-support/…` paths because GitHub Pages
serves it at whatever URL was missing; update them if the site ever moves to a
custom domain.

## TODO

- [ ] **Set `STORE_URLS["store-ios"]`** at the top of the script in
      `join/index.html` to `https://apps.apple.com/app/id6828979440` on the day the
      iOS app goes on sale, not before: the link errors until then (1.0.0 has been in
      App Review since 2026-11-09 and is released automatically once approved). Until
      then the App Store button is hidden; the text still says to get the app from the
      App Store or Google Play. `store-android` is already set to
      `https://play.google.com/store/apps/details?id=com.branicio.lightfast`
      (1.0.0 went to Google Play's production track on 2026-11-09).

## Links

- [Support](https://branicio.github.io/lightfast-support/)
- [Privacy Policy](https://branicio.github.io/lightfast-support/privacy.html) · [pt](https://branicio.github.io/lightfast-support/privacy.html#portugues) · [es](https://branicio.github.io/lightfast-support/privacy.html#espanol) · [fr](https://branicio.github.io/lightfast-support/privacy.html#francais) · [it](https://branicio.github.io/lightfast-support/privacy.html#italiano) · [de](https://branicio.github.io/lightfast-support/privacy.html#deutsch)
- [Terms of Use](https://branicio.github.io/lightfast-support/terms.html) · [pt](https://branicio.github.io/lightfast-support/terms.html#portugues) · [es](https://branicio.github.io/lightfast-support/terms.html#espanol) · [fr](https://branicio.github.io/lightfast-support/terms.html#francais) · [it](https://branicio.github.io/lightfast-support/terms.html#italiano) · [de](https://branicio.github.io/lightfast-support/terms.html#deutsch)

## Contact

braniapps@gmail.com
