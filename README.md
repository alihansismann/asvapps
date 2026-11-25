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
   the privacy policy and the home page). Nothing else differs from the source pages.
4. Links between pages are already relative (`privacy.html`, `../index.html`), so they need no
   change to work under the `/asvapps/` sub-path.
5. Commit and push to `main`; GitHub Pages publishes from the root of `main`.
