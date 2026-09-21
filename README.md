# fezzaioussama.github.io

> Personal portfolio site — AI R&D engineer, computer vision, ML, and LLMs. Single page, no framework, no build step.

Live at **[fezzaioussama.github.io](https://fezzaioussama.github.io)**, served
straight from this repository by GitHub Pages.

Three files do the whole job: `index.html`, `index.css`, `index.js`. There is no
bundler, no dependency install, and nothing to compile — which is the point for
a site that should still build itself in five years.

## Run it locally

Open `index.html` in a browser. That's it.

For a local server (so relative paths and the CV download behave exactly as they
do in production):

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## Deploy

Push to `main`. GitHub Pages serves the repository root — no workflow, no build
step, no `gh-pages` branch.

## Structure

```
index.html        # All content — every section, plus page-specific <style>
index.css         # Design system: CSS custom properties, layout, components
index.js          # Typing animation, scroll reveal, smooth scroll, mobile nav
assets/
  oussama.png     # Profile photo — also the favicon and Open Graph image
  CV_Oussama_Fezzai.pdf
```

## Sections

`#about` · `#experience` · `#skills` · `#education` · `#projects` ·
`#certifications` · Publications · `#contact`

## Design system

The palette lives in `:root` custom properties in `index.css` — change a
variable, change the whole site:

| Token | Value | Role |
|---|---|---|
| `--bg-primary` / `--bg-secondary` / `--bg-tertiary` | `#0a0a0c` → `#1c1c22` | Dark layered background |
| `--accent-primary` | `#7c4dff` | Purple |
| `--accent-secondary` | `#00d4ff` | Cyan |
| `--accent-gradient` | 135° purple → cyan | Headings, highlights |
| `--text-primary` / `--text-secondary` / `--text-muted` | `#ffffff` → `#6b6b76` | Type hierarchy |
| `--glass-bg` / `--glass-border` | translucent white | Frosted-glass cards |

Typeface is Inter, loaded from Google Fonts with `preconnect` hints.

## Behaviour (`index.js`)

| Feature | Notes |
|---|---|
| Typing animation | Cycles five role phrases in the hero — 60 ms per character, 30 ms deleting, 2 s hold at full phrase |
| Scroll reveal | Elements with `.reveal` fade in as they enter the viewport |
| Smooth scrolling | JS fallback for Safari and older browsers, backing up CSS `scroll-behavior` |
| Mobile nav | Hamburger toggle that closes on link click |

## Editing

- **Content** — edit `index.html` directly; each section is a plain `<section id="…">`.
- **Colours and spacing** — edit the custom properties at the top of `index.css`.
- **Role phrases** — the `phrases` array at the top of `index.js`.
- **CV** — replace `assets/CV_Oussama_Fezzai.pdf`, keeping the filename so the
  download link keeps working.

Note that `index.html` also carries a page-specific `<style>` block for the hero
and profile image, separate from `index.css`.

## SEO

`index.html` sets description and keyword meta tags, `theme-color`, and Open
Graph tags (`og:type`, `og:title`, `og:description`, `og:image`) so shared links
render a card. Update these alongside any significant content change.
