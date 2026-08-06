# SHANER & CO. — static preview

Drop this whole folder into the repo root and enable GitHub Pages on the branch.
No build step, no dependencies — plain files a browser can open.

## What serves what

| URL | Serves |
| --- | --- |
| `/` | router: picks the build from the device |
| `/desktop.html` | desktop build |
| `/mobile.html` | mobile build |
| `/?v=desktop` / `/?v=mobile` | force either build on any device |

Use `?v=` to check the mobile build from a desktop browser, and vice versa.

## Files

```
index.html        router (device detect + ?v= override)
desktop.html      desktop build — the whole site, one file
mobile.html       mobile build — the whole site, one file
support.js        runtime both builds load
image-slot.js     image placeholder element
fonts/            Antique Legacy — Thin 300, Book 400, Bold 700
images/
  md/ 01–12       Mandeville Residence
  lt/ 01–11       La Terraza
  arch/ 01–33     Vault / archive
.nojekyll         stops Pages from filtering files
```

## Where to change things

Both builds are one file each. In `desktop.html`:

| To change | Look for |
| --- | --- |
| project list, order, status | `const PROJECTS` |
| project type + year (List view) | `const META` |
| grid cover per project | `const COVERS` |
| specs, body copy, areas | `const COPY` |
| archive images | `const ARCHIVE` |
| page edges, image top, caption band | `:root` — `--pad`, `--img-top`, `--cap-band` |
| card size range on the Scale dial | `cardDial()` — `MIN` / `MAX` |
| deck fan angle, depth, overlap | `perspDeck()` — `SHAPE`, `OVER`, `GAP` |
| list hover magnification | `[data-row]:hover` rules |
| intro timing | `runIntro()` — settle, pause, travel |

`mobile.html` uses the same names, so a copy change is the same edit in both.

## Adding project images

Drop files into `images/<project>/` numbered in order, then add the paths to that
project's entry in `PROJECTS`. Aspect ratios are read from the files themselves —
nothing to declare, portrait and landscape both work.
