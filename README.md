# morsel-site

Landing page and privacy policy for Morsel. Plain HTML + CSS, no build step.
Layout follows the "Record" Behance case study: huge headlines, serif ledes, rounded image tiles,
dark sections, five store screenshots — with a Google Play CTA after every section.

```
index.html     landing page
privacy.html   privacy policy (put this URL in Play Console)
styles.css     shared styles; colours match the app (src/lib/theme.tsx)
img/           icon, Google Play badge, link-preview image
img/photos/    lifestyle photos (you supply)
img/screens/   phone mockups (you supply)
```

Preview: open `index.html` in a browser. Every empty slot shows its file name and size.

## Image slots

Drop a file with the exact name below and it appears; no code changes needed.
Sizes are what the slot is shaped for (2× for sharp screens); close is fine, the image is cropped to fit.

| Section | File | What | Size |
|---|---|---|---|
| 1 Hero | `photos/hand-phone.jpg` | Hand holding the phone, Morsel on screen | 1280 × 1460 |
| 1 Hero | `photos/watch.jpg` | Watch close-up, steps on the face | 1600 × 1460 |
| 3 Goals | `screens/goal-lose.png` | Phone mockup, top part only (cut at the bottom), transparent | 900 × 1100 |
| 3 Goals | `screens/goal-gain.png` | same | 900 × 1100 |
| 4 Workouts | `screens/workout.png` | Phone mockup on a grey tile (fills the tile) | 1200 × 1400 |
| 5 Sync | `photos/watch-on-wrist.jpg` | Watch on a wrist | 1400 × 1500 |
| 7 After every day | `photos/progress-photos.jpg` | Phone in hand, progress-photo compare on screen | 1400 × 1500 |
| 8 Forecast | `screens/forecast.png` | Phone mockup on a white tile (fills the tile) | 1200 × 1400 |
| 9 Inside the app | `screens/ui-home.png` | Phone mockup, transparent | 900 × 1200 |
| 9 Inside the app | `screens/ui-log.png` | Phone mockup, transparent | 900 × 1200 |
| 9 Inside the app | `screens/ui-progress.png` | Phone mockup, transparent | 900 × 1200 |
| 11 Five screens | `screens/shot-plan.png` | Phone mockup | 700 × 1100 |
| 11 Five screens | `screens/shot-food.png` | Phone mockup | 700 × 1100 |
| 11 Five screens | `screens/shot-watch.png` | Phone + watch mockup | 700 × 1100 |
| 11 Five screens | `screens/shot-day.png` | Phone mockup: a finished day's verdict | 700 × 1100 |
| 11 Five screens | `screens/shot-progress.png` | Phone mockup | 700 × 1100 |

The sync diagram in section 5 (watch + phone → Morsel) is drawn in code; no image needed.

Phone mockups (`screens/`) should be PNGs with a transparent background; they sit at the bottom
of their card. Photos (`photos/`) fill their rounded tile edge to edge.

To use a different name or format (e.g. `.webp`), change the `src` on that `<img>` in `index.html`.

## Live URLs

- Site: https://nofilbashir.github.io/morsel-site/
- Privacy policy (Play Console → App content → Privacy policy): https://nofilbashir.github.io/morsel-site/privacy.html

The in-app policy (`100-days/src/app/privacy.tsx`) carries the same words; change both together.

## Hosting (GitHub Pages)

First time:

1. github.com/new → name `morsel-site`, **Public**, no README → Create.
2. Push this folder:
   ```bash
   cd ~/Desktop/morsel-site
   git remote add origin https://github.com/Nofilbashir/morsel-site.git
   git push -u origin main
   ```
   When git asks for a password, paste a personal access token
   (github.com/settings/tokens → Generate new token (classic) → tick `repo`).
3. Repo → Settings → Pages → Source "Deploy from a branch" → branch `main`, folder `/ (root)` → Save.
4. About a minute later the site is live at the URLs above.

Every update after that:

```bash
cd ~/Desktop/morsel-site
git add . && git commit -m "Update site" && git push
```

Bump `styles.css?v=N` in both HTML files when the CSS changes, so phones don't keep the old copy.

For a custom domain later: Settings → Pages → Custom domain, plus a CNAME record pointing at
`nofilbashir.github.io`. Then update the privacy URL in Play Console and in `privacy.tsx`.
