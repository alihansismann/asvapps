# ASV Apps — privacy policy and terms pages

Static pages served with GitHub Pages at <https://alihansismann.github.io/asvapps/>.

| Page | Address |
| --- | --- |
| Turnela — home | `/asvapps/` |
| Turnela — privacy policy | `/asvapps/privacy` (also `/privacy.html`) |
| Turnela — terms of use | `/asvapps/terms` (also `/terms.html`) |
| Goncela — home | `/asvapps/goncela/` |
| Goncela — privacy policy | `/asvapps/goncela/privacy` (also `.html`) |
| Goncela — terms of use | `/asvapps/goncela/terms` (also `.html`) |

Contact: asvapps.dev@gmail.com

## How this folder is produced

This folder is a hand-adapted copy of the generated site; it is not built by a script.

1. Source pages (generated elsewhere, kept outside this repository):
   - Turnela: `index.html`, `privacy.html`, `terms.html`
   - Goncela: `goncela/index.html`, `goncela/privacy.html`, `goncela/terms.html`
2. Copy them here unchanged, keeping the folder layout, and keep the empty `.nojekyll` file.
3. Apply one change only — the site address (byte-preserving, line endings untouched):

   ```sh
   sed -b -i \
     -e 's#asvapps\.pages\.dev#alihansismann.github.io/asvapps#g' \
     -e 's#\(https://alihansismann\.github\.io/asvapps\)\(["<]\)#\1/\2#g' \
     index.html privacy.html terms.html goncela/*.html
   ```

   This rewrites 14 lines in 4 files (the address shown in the text and the absolute links to
   the privacy policy and the home page).
4. In the two privacy pages only (`privacy.html` section 13, `goncela/privacy.html` section 16,
   Turkish and English), correct the hosting paragraph by hand, because this copy is served by
   GitHub Pages and not by the original host:
   - "Cloudflare Pages" becomes "GitHub Pages (GitHub, Inc.)".
   - The sentence about the host processing visitors' IP addresses becomes: "When the site/page
     is visited, GitHub logs and stores the visitor's IP address in its own systems for security
     purposes", linking to the GitHub Privacy Statement
     (<https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement>).
     Basis: GitHub Docs, "What is GitHub Pages?" → "Data collection".
   - The statements about no cookies, analytics, ads or forms, the section headings and their
     `id` anchors stay as they are.
   - Under the existing paragraph of the "changes" section (Turnela 14, Goncela 17) add one
     line: "Güncelleme: 25 Kasım 2026 — site barındırıcısı ve adresi değişti." /
     "Updated: November 25, 2026 — site host and address changed."
   - Effective dates and version numbers are not changed. Keep each file's existing line endings.

   Once the source pages themselves carry these sentences, this step is no longer needed.
5. Nothing else differs from the source pages. Links between pages are already relative
   (`privacy.html`, `../index.html`), so they need no change to work under the `/asvapps/` sub-path.
6. Commit and push to `main`; GitHub Pages publishes from the root of `main`.
