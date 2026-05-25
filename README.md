# Milton MS CS — Codio Guide Theme

A custom **Override Guides CSS** theme for [Codio](https://docs.codio.com/), styled to
match Milton Academy's middle school computer science brand: a warm parchment surface,
Crimson Pro headings in Milton blue with hand-drawn orange accents, JetBrains Mono code
blocks, and styling for all of Codio's callout types, tables, lists, and collapsibles.

> Origin: designed in [Claude Design](https://claude.ai/design) and handed off for
> implementation. The stylesheet is the production artifact; `preview.html` is a mock
> Codio Guide pane for previewing the theme without deploying.

## Files

| File | Purpose |
|------|---------|
| `codio-milton.css` | **The theme.** This is the file Codio loads. Self-contained — webfonts via Google Fonts, sketch accents inlined as SVG data URIs. |
| `preview.html` | A mock Codio Guide pane showing a sample lesson styled by the theme. Open it to preview changes. |
| `preview-assets/` | Milton logo, seal, and sketch accents (brand assets; not required by the theme itself). |

## Hosted URLs (GitHub Pages)

Pages serves the repo root, so the files are reachable at:

- **Theme CSS:** `https://bsitkoff.github.io/milton-codio-css/codio-milton.css`
- **Preview:** `https://bsitkoff.github.io/milton-codio-css/preview.html`

## Set it up in Codio

This is a **full override** — it replaces Codio's default guide styling entirely.

1. In Codio, go to **Courses → your course → Course Details**.
2. Find the **Override Guides CSS URL** field.
3. Paste:
   ```
   https://bsitkoff.github.io/milton-codio-css/codio-milton.css
   ```
4. **Save.**

> ⚠️ Use the **Override** field, *not* "Extra Guides CSS URL". This stylesheet is a full
> replacement and is not designed to layer on top of Codio's defaults.

Docs: [Setting course-level custom CSS](https://docs.codio.com/instructors/authoring/guides/markdown_content.html#setting-course-level-custom-css)

## Updating the theme

GitHub Pages redeploys automatically on every push to `main`.

```bash
# edit codio-milton.css, then:
git add codio-milton.css
git commit -m "Tweak callout colors"
git push
```

Pages takes ~1 minute to rebuild. Codio fetches the CSS in the student's browser, so a
hard refresh (or a cache-busting `?v=2` on the URL) may be needed to see changes
immediately.

## Previewing locally

```bash
# from the repo root
python3 -m http.server 8000
# then open http://localhost:8000/preview.html
```

Everything inside the middle `.rendered-markdown` pane is what the theme controls; the
surrounding Codio chrome in the preview is just a mock for context.

## What's in the theme

- Parchment surface (`#fbf8f2`); Crimson Pro headings in Milton blue (`#003E7E`) with
  hand-drawn orange underlines under H1/H2.
- Body in Crimson Pro at 18px / 1.65; **bold** renders in Milton blue.
- Light code blocks on warm parchment with JetBrains Mono, covering both highlight.js
  (`.hljs-*`) and Pygments/kramdown (`.highlight .k`) class names.
- All 14 Codio callout types (`info`, `important`, `warning`, `topic`, `definition`,
  `challenge`, `guidance`, `meetup`, `hackathon`, `create`, `calendar`, `growthhack`,
  `xdiscipline`, `debugging`) with accent bars, tinted backgrounds, and labeled chips.
- Numbered lists with hand-drawn circle counters; bullets as small orange diamonds.
- Navy-header tables with parchment zebra striping, styled `<details>`/`<summary>`
  collapsibles, a print stylesheet for clean handouts, and a narrow-viewport layout.

## Notes

- If a real Codio lesson uses slightly different callout class names than expected, the
  CSS is resilient (`.callout-info`, `.codio-callout-info`, `[class*="callout-info"]`).
  If a callout type doesn't pick up its color, grab the element's class from devtools and
  add the matching selector.

---

Maintainer: Bridget Sitkoff — Milton Academy MS CS
