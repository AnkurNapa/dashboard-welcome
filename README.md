# Dashboard Welcome Screen

A single self-contained `index.html` — a vintage-editorial wine welcome splash
(burgundy + cream, Fraunces serif, brass seal). Built to be hosted on GitHub
Pages and embedded inside a Tableau dashboard via a **Web Page** object.

No build step, no dependencies. Fonts load from Google Fonts (with serif
fallbacks if offline).

## 1 — Host it on GitHub Pages

1. Create a new GitHub repo (e.g. `dashboard-welcome`) and add `index.html` to it.
2. Repo **Settings → Pages** → *Build and deployment* → Source: **Deploy from a branch**
   → Branch: **main**, folder: **/ (root)** → Save.
3. After ~1 minute your page is live at:
   `https://<your-username>.github.io/<repo-name>/`
   (this is HTTPS — required for Tableau).

## 2 — Embed it in Tableau

1. Open your dashboard. From the left **Objects** panel, drag a **Web Page**
   object onto the dashboard.
2. Paste your GitHub Pages URL (the `https://…github.io/…` link) and click OK.
3. Resize/position the region. The splash is responsive and centers itself, so
   it looks right whether the region is wide or compact.
4. To refresh after editing the page: right-click the object → it reloads on
   open, or re-enter the URL.

> Tableau only embeds **HTTPS** pages — GitHub Pages serves HTTPS automatically,
> so you're covered.

## 3 — Customize

Open `index.html` and edit the text between the
`===== EDIT TEXT BELOW =====` … `===== END EDIT TEXT =====` markers:

| What | Where |
|---|---|
| Brand line | `<p class="kicker">Estate Analytics</p>` |
| Headline (two lines) | `.l1` ("Welcome to the") and `.l2` ("Vintage Report") |
| Subtitle | `<p class="sub">…</p>` (wrap key words in `<em>…</em>`) |
| Button label | inside `<a class="enter">…</a>` |
| Footer | `<p class="foot">…</p>` |

Colors live in the `:root` block at the top of `<style>` (`--wine`, `--cream`,
`--brass`, …) — change those to retheme everything.

### About the "Enter the dashboard" button

The button's link is `href="#"` by default (does nothing). Set it to any URL:

```html
<a class="enter" href="https://your-link-here">
```

Note: clicking a link inside a Tableau Web Page object loads that URL **inside
the same region**. To actually jump between Tableau dashboards, use Tableau's
own navigation **Button** objects (see `Dashboard Navigation.twbx`). Point this
`href` at an external page or a published Tableau view URL if you want it to
open something.
