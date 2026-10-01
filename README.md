# MECH 2030 Lecture Notes

Typeset lecture notes for MECH 2030 (Solid Mechanics), published as a website
with one PDF per lecture plus a combined PDF of all notes.

## Repository layout

```
mech2030notes.sty           shared macros and TikZ styles (edit once, applies everywhere)
lectures/wXXlY.tex          one complete LaTeX document per lecture
build_site.py               compiles everything and writes the website into site/
.github/workflows/          GitHub Action that runs build_site.py and publishes site/
```

## One-time setup

1. Create a new repository on GitHub (e.g. `mech2030`) and push this folder to its
   `main` branch.
2. In the repository, go to **Settings → Pages** and set **Source** to
   **GitHub Actions**.
3. Push any commit (or run the workflow from the **Actions** tab). After a few
   minutes the site is live at `https://<user-or-org>.github.io/<repo>/`.
4. Edit the course settings (`COURSE_CODE`, `TERM`, `INTRO`, ...) at the top of
   `build_site.py`.

## Adding a new lecture

1. Copy an existing lecture file, e.g. `lectures/w06l2.tex` → `lectures/w06l3.tex`.
2. Change the `\lecture{week}{lecture}{Title}` line and write the content.
3. Commit and push. The site rebuilds automatically; the new lecture appears on the
   home page under its week, with the date it was first committed.

Each lecture file compiles on its own in any LaTeX editor (Overleaf, TeXShop,
VS Code, ...), as long as `mech2030notes.sty` is in the folder above it or on
your TeX path. (In most editors, simply compile from the repository root.)

### Hiding a lecture until it's ready

Add a line containing only `% draft` to the lecture file. It is skipped by the
website and the combined PDF. Delete the line to publish.

### Changing the date shown on the website

By default the date is when the file was first committed. To override it, add a
line such as `% posted: 2026-09-02` to the lecture file.

## Building locally

Requires a TeX distribution with `latexmk` and Python 3:

```
python build_site.py            # full build into site/
python build_site.py --no-pdf   # only regenerate index.html
```

Then open `site/index.html` in a browser.
