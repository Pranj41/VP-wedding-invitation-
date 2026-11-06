# Varsha & Pranjal — Wedding Invitation

A complete static invitation in HTML, CSS, vanilla JavaScript and Canvas. No npm, framework, server, database, API key or build step is required.

## Open it locally

Double-click `index.html`, or open it in a current browser. Fonts use Google Fonts when online; built-in serif and sans-serif fallbacks work offline. All photographs, video and scripts are local. The introductory video plays once per browser session; a direct section link skips it. Use a fresh browser session to replay it. Visitors who prefer reduced motion skip the intro automatically.

## Project files

```text
web/
├── index.html                    Page structure and social metadata
├── css/
│   └── style.css                 Responsive layouts, design tokens, animations
├── js/
│   ├── main.js                   Configuration, intro, gallery, music, sharing, ICS
│   ├── scratch.js                Pointer-driven Canvas scratch card, 55% reveal
│   └── countdown.js              Countdown with an explicit India timezone offset
├── assets/
│   ├── logo/
│   │   ├── wedding-logo.png       Still at 8 seconds from your supplied animation
│   │   └── wedding-logo-animation.mp4
│   ├── photos/
│   │   ├── hero-couple.jpg
│   │   ├── couple-01.jpg
│   │   ├── couple-02.jpg
│   │   ├── couple-03.jpg
│   │   └── couple-04.jpg
│   ├── music/
│   │   └── README.txt             Instructions for optional wedding-music.mp3
│   ├── wedding-preview.jpg       Supplied ceremony photograph, unaltered
│   └── favicon.svg               Lightweight VP monogram favicon
├── checks/                       Optional developer browser checks, not required to host
│   ├── browser-tools.ps1
│   ├── run-browser-checks.ps1
│   ├── run-mobile-checks.ps1
│   ├── results.json
│   └── mobile-results.json
├── .gitignore
├── .nojekyll
└── README.md
```

Local screenshots, the test calendar and the headless browser profile in `checks/` are ignored by Git. Omit the entire `checks/` folder when uploading by hand. It is not part of the website runtime.

## Your supplied media

All four original photographs were copied byte-for-byte, preserving faces, colour and composition. No image generation, face modification or photo processing was used. The portrait with white margins retains those margins. The ceremony photo is reused for the hero, fourth story photograph, closing screen and social preview.

| Website asset | Supplied photograph | Original dimensions |
| --- | --- | --- |
| `hero-couple.jpg`, `couple-04.jpg`, `wedding-preview.jpg` | Image without a parenthesized number; seated ceremony | 1600 × 1066 |
| `couple-01.jpg` | Image (2); holding hands on the steps | 960 × 1280 |
| `couple-02.jpg` | Image (3); seated on the steps | 1594 × 1600 |
| `couple-03.jpg` | Image (1); standing portrait in formal attire | 1024 × 1280 |
| `wedding-logo-animation.mp4` | Supplied WhatsApp video | 1024 × 576, 24 fps, about 10 seconds |
| `wedding-logo.png` | Unaltered full frame at 8 seconds from the supplied video | 1024 × 576 |

No required image or video remains to be added. Optional: supply a separate transparent logo if you prefer it to the floral still. Optional: supply your own music MP3. The website handles missing images and unavailable video gracefully.

## Replace photographs

Replace files under `assets/photos/` while keeping the filenames, or edit `gallery` and `heroImage` in `js/main.js`. Each gallery entry has its own `src`, descriptive `alt`, natural `width` and `height`, story title and caption. Update those dimensions when replacing an image. Portrait, landscape and square gallery images use their natural proportions. Family photographs follow the gallery configuration.

For best results, use clear originals around 1600–2400 pixels on the long edge. A landscape hero around 2000 × 1333 works well with this layout. Keep both faces together toward the right side, where the hero text has room on the left; use `heroPosition` and `heroMobilePosition` to adjust CSS cropping for a different composition. Gallery photographs need no fixed aspect ratio. The lightbox always shows the whole photograph.

## Replace the logo and video

Replace `assets/logo/wedding-logo.png` with your logo, ideally a PNG with a transparent background, about 800–1200 pixels wide. Both portrait and landscape logo shapes are contained without distortion. If the logo is missing, the typographic initials remain visible.

Replace `assets/logo/wedding-logo-animation.mp4` with an MP4 that plays in browsers, preferably H.264 video, 720p or 1080p, around 5–12 seconds and below 5 MB. The provided 10-second file is about 1.7 MB. It plays muted, inline and without looping. If your replacement is longer, adjust `introMaxSeconds` in the configuration. Failed playback shows the logo and continues; the intro always has a Skip Intro button.

## Add optional music

1. Add `assets/music/wedding-music.mp3` using audio you have permission to use.
2. Change `musicEnabled: false` to `musicEnabled: true` in `js/main.js`.
3. The floating music button appears. Playback begins only when a guest taps it, loops and uses 30% volume. Missing audio hides the control gracefully.

## Edit wedding details

The `weddingConfig` object at the top of `js/main.js` controls names, parents, hashtag, dates, images, event details, venue, map URL and music. The supplied wedding target is `2026-12-12T14:00:00+05:30`, which equals 08:30 UTC. Retain an explicit timezone offset when changing it.

The scratch card reveals at approximately 55% erased coverage; the visible keyboard-accessible button also reveals it. It intentionally starts concealed on each page load. Its countdown appears only after revelation, updates every second and changes to the wedding-day message at the target.

`celebrationStart` and `celebrationEnd` control the downloaded calendar event: 11 December at noon to 12 December at 11 PM IST. The end is a practical calendar duration for the two-day invitation, not a stated reception closing time; adjust it if desired. Individual event times appear in the calendar description. Downloads use UTC timestamps, CRLF lines and escaped, UTF-8-safe folded content.

Also update the static `<title>`, description, Open Graph tags and initial HTML fallback text if changing this invitation to a different couple or date. Social crawlers typically read HTML without running JavaScript.

## Update the map

Edit `mapUrl` in `weddingConfig`. The supplied link searches Google Maps for The Mark Club & Resort, Dhanora, Bhilai. Replace it with the exact venue's Google Maps share link when available. The decorative venue drawing is an illustration, not a photograph of the resort. No Maps API is used.

## Publish with GitHub Pages

1. Create a GitHub repository, for example `varsha-pranjal-wedding`. A public repository works with GitHub Free.
2. Upload the **contents of `web/`** to the repository's `main` branch. `index.html` must be at the repository root, alongside `css/`, `js/`, `assets/` and `.nojekyll`. Do not nest everything inside another `web/` directory. Omit `checks/` when uploading manually.
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment → Source**, select **Deploy from a branch**.
5. Select branch **main** and folder **/(root)**, then click **Save**.
6. Wait for GitHub's Pages deployment to finish. Open the URL shown there, usually `https://USERNAME.github.io/REPOSITORY-NAME/`.
7. Set `siteUrl` in `js/main.js` to that complete public URL. In `index.html`, change `og:image` to the full public image URL, e.g. `https://USERNAME.github.io/REPOSITORY-NAME/assets/wedding-preview.jpg`. Add an `og:url` meta tag with the public invitation URL if desired. Commit the changes.
8. Verify the public page on a phone and share its HTTPS address. Native sharing is used when available, with clipboard and selectable-link fallbacks. Local `file://` paths are never shared as invitation URLs.

Runtime file references are relative, so repository subpaths work. Social preview metadata is the exception: supply a full public image URL for messaging crawlers. A dedicated 1200 × 630 social card is optional; the supplied original photograph already works as the initial preview.

Official instructions: [Configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Optional custom domain

In **Settings → Pages → Custom domain**, enter the domain you own and save it. For a subdomain such as `wedding.example.com`, create a DNS `CNAME` pointing to `USERNAME.github.io` (without the repository path). For an apex domain, follow GitHub's current A/AAAA or ALIAS instructions. After DNS and certificate provisioning complete, enable **Enforce HTTPS**. Update `siteUrl` and the static Open Graph image URL to the custom domain. Keep the `CNAME` file GitHub adds for branch-based deployment.

Official instructions: [Managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

## Browser verification

The optional `checks/` scripts exercise the actual page in headless Microsoft Edge through its local DevTools connection. No Node.js or production dependencies are needed. They cover desktop/mobile layouts, mouse/touch scratch gestures, keyboard date reveal, countdown timezone and arrival state, ICS bytes, gallery arrows/swipe/Escape, missing images, intro success/failure, optional music and reduced motion. JSON reports record the results.

To repeat checks, start a dedicated headless Edge instance with remote debugging on local port 9222 and this page open at `#home`, then run the check scripts with a process-only PowerShell execution-policy override. The scripts are developer utilities; normal visitors need only the static site. Mobile checks emulate a touchscreen in Edge; physical iPhone/Safari and Android device verification is still recommended before sending invitations.

## Floral and Indian-inspired decorative artwork

The invitation now includes locally hosted CC0 lotus, floral and flowering-branch SVGs sourced from SVG Repo. These appear as a hero ornament, lotus dividers, a repeating celebration border and subtle floral corners. Their colours and mobile sizes are controlled by the final decorative-artwork section in `css/style.css`.

Files: `assets/decorations/lotus.svg`, `floral-ornament.svg`, `flower-branch.svg`, and `SOURCES.md`. Full source links, license references and modifications are recorded in [artwork credits](assets/decorations/SOURCES.md). The ornaments add approximately 20 KB and require no extra JavaScript or network calls to an asset provider.

## Scratch-card logo and lettering

The scratch reveal uses your supplied transparent peacock monogram at `assets/logo/scratch-monogram.png`, configured independently through `scratchLogoImage` in `js/main.js`. The remaining site logos use `logoImage`. The uploaded monogram was copied without modification.

“Save the date” is live text in the locally hosted Great Vibes font, followed by the wedding dates and couple details. Font source: https://github.com/google/fonts/tree/main/ofl/greatvibes. The SIL Open Font License is included at `assets/fonts/GreatVibes-OFL.txt`. The lettering reference images are used for style guidance; the card does not embed their screenshots.
