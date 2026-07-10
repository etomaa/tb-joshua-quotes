# GOSW Dawn Design System — Restyle Log

Technical record of the visual restyle applied to `index.html` on 2026-07-11, for reproducibility on other sites sharing this identity (e.g. spiritworshipgen.org) and so future changes can be diffed against the original intent.

## Original request (verbatim)

> I want to restyle this TB Joshua quotes page with a design system called "GOSW Dawn" —
> the same identity used on spiritworshipgen.org, for brand consistency across my two sites.
>
> First, explore this project's structure (it's likely a static single index.html) and show
> me how CSS is currently organized before changing anything.
>
> Then apply this design system:
>
> ### Palette (light + dark, as CSS custom properties with a light/dark toggle)
>
> Light:
> ```
> --paper: #F3EFE6;       /* page background */
> --surface: #FBF9F3;      /* cards, navbar */
> --surface-2: #EFEADF;    /* code/tag fills */
> --ink: #241F17;          /* body text */
> --muted: #6A6153;
> --faint: #8B8273;
> --gold: #9C6B12;         /* accent — links, active states */
> --gold-bright: #B8801F;  /* hover */
> --green: #456B3E;        /* secondary accent — tags/categories */
> --hairline: #E4DDCE;     /* dividers, borders */
> --glow: rgba(184, 128, 31, 0.10);
> --img-shadow: rgba(36, 31, 23, 0.10);
> ```
>
> Dark:
> ```
> --paper: #15120C;
> --surface: #1E1911;
> --surface-2: #262015;
> --ink: #EEE7D7;
> --muted: #A99C85;
> --faint: #8A7E68;
> --gold: #E7B24E;
> --gold-bright: #F0C36A;
> --green: #93AC86;
> --hairline: #332C1F;
> --glow: rgba(231, 178, 78, 0.09);
> --img-shadow: rgba(0, 0, 0, 0.45);
> ```
>
> Define these as `:root` custom properties (light values default), override under
> `@media (prefers-color-scheme: dark)`, and also override under `:root[data-theme="dark"]` /
> `:root[data-theme="light"]` so a manual toggle can win over OS preference in both directions.
> Add a light/dark toggle control if one doesn't already exist.
>
> ### Typography — system stacks only, no web-font downloads
> ```
> --font-serif: "Iowan Old Style", "Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif;
> --font-sans: system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
> --font-mono: "SF Mono", "Cascadia Code", ui-monospace, Consolas, "Liberation Mono", monospace;
> ```
> Headings and any pull-quote/lead text use `--font-serif` (natural case, not uppercase). Body
> and UI chrome use `--font-sans`. Labels, tags, dates, and metadata use `--font-mono`, uppercase,
> with letter-spacing ~0.1em.
>
> ### Component rules
> - **Quote cards** (this is the big one — every TB Joshua quote should read like a manuscript
>   clipping): gold left border (3px solid var(--gold)), no background fill, serif italic text
>   at ~1.13rem, line-height 1.55, padding-left ~1.25rem, attribution in --muted, non-italic,
>   smaller size.
> - **Category/topic tags** (if present): mono font, sage-green background at ~14% opacity,
>   sage-green text, 1px sage-green border at ~32% opacity, 6px border-radius, hover fills
>   solid green with paper-colored text.
> - **Header/nav**: surface background, hairline bottom border, serif brand/site name, links in
>   muted color that go gold on hover/active.
> - **Dividers**: 1px solid var(--hairline), not a heavier default rule.
> - **Cards/images**: 12px border-radius, soft two-layer shadow using var(--img-shadow).
> - Keep the search/filter functionality exactly as it works now — this is a styling pass only,
>   not a functional rewrite.
>
> Build cleanly: don't collapse the light and dark styling into one guess-and-invert pass — give
> dark mode the same care (check contrast, make sure gold and green still pop against the dark
> ground). Show me the result before considering it done.

## Pre-existing state (as found)

- Single tracked file: `index.html` (751 lines). `tb_joshua_quotes.html` is a gitignored local working copy, untouched by this change.
- All CSS lived in one `<style>` block in `<head>` (no external stylesheet, no build step).
- Fonts were loaded from Google Fonts (`Cormorant Garamond`, `Outfit`) via `<link>`.
- A dark-mode toggle already existed (`#themeBtn` → `toggleTheme()`), driven by a `data-theme` attribute on `<html>` plus `localStorage`, with an OS-preference fallback in `initTheme()`. This was reused as-is — no JS changes.
- Palette was a single hardcoded set (`--navy`, `--navy2`, `--gold`, `--gold2`, `--cream`, `--text`, `--muted`, `--border`, `--hl`) with one dark override block on `html[data-theme="dark"]` (no `@media (prefers-color-scheme: dark)`, no explicit `[data-theme="light"]` block).
- Quote data (`Q` array) is `{id, text}` only — **no category/tag field exists in the data model.**

## Changes made

### 1. Fonts
Removed both Google Fonts `<link>` tags. Replaced with the three system stacks (`--font-serif`, `--font-sans`, `--font-mono`) as plain `:root` custom properties (theme-independent).

### 2. Palette + theme cascade
Replaced the old token set with the GOSW Dawn tokens verbatim (see palette above), implemented as three cascading blocks in this order:
1. `:root { ... }` — light values (default)
2. `@media (prefers-color-scheme: dark) { :root { ... } }` — dark values, follows OS preference
3. `:root[data-theme="dark"] { ... }` / `:root[data-theme="light"] { ... }` — explicit override, wins in both directions once the user has toggled manually

Added one extra token beyond the spec, `--flash`, to replace a hardcoded flash-highlight color that was tuned only for the old light palette (see below) — themed the same way (light/dark values), so the "scroll to quote" flash reads correctly in both modes instead of relying on a fixed rgba.

### 3. Selector-by-selector restyle (same ids/classes throughout — no JS hooks changed)

| Selector | Before | After |
|---|---|---|
| `body` | `Outfit`, `--cream`/`--text` | `--font-sans`, `--paper`/`--ink` |
| `header` | navy bg + heavy `box-shadow` | `--surface` bg, `1px solid var(--hairline)` bottom border |
| `.brand h1` | Cormorant Garamond, `--gold2` | `--font-serif`, `--gold-bright` |
| `.brand p` | plain small text | `--font-mono`, uppercase, `letter-spacing:.1em`, `--faint` |
| `.sw input` (search box) | translucent-white-on-navy | `--surface-2` bg, `--hairline` border, `--ink` text |
| `.mb span` / `.gw label` (meta/labels) | translucent white | `--font-mono`, uppercase, `--faint` |
| `.gbtn` | navy text on gold | `--surface`-colored text on gold (navy no longer exists) |
| `.qi` (quote card) | flex row, bottom-border divider only | **`border-left:3px solid var(--gold)`**, no fill at rest, `background:var(--glow)` on hover, `padding-left:1.25rem`; dropped the old `:first-child` top-border (doesn't suit a left-rail card) |
| `.qn` (quote number) | bold gold serial number | repurposed as the per-card mono/uppercase meta line (`--muted`) — see note below |
| `.qt` (quote text) | Cormorant Garamond, not italic, 1.12rem/1.7 | `--font-serif`, **italic**, 1.13rem/1.55, `--ink` |
| `.qt mark` (search highlight) | `--hl` (removed var) | `--glow` |
| `.qa button` | navy hover text | gold/`--gold-bright` hover |
| `.qa button.ok` (copied state) | hardcoded `#22c55e`/`#16a34a` | `--green` (themed, contrast-correct in both modes) |
| `#toast` | flat navy box | `--surface` bg, **12px radius**, **two-layer shadow via `--img-shadow`**, gold left border |
| `footer` | navy bg | `--surface` bg, `--hairline` top border, `--faint` text |
| `.tbtn` (theme toggle button) | translucent white border | `--hairline` border, `--muted`/gold-on-hover |
| `@keyframes fl` (flash-on-scroll) | hardcoded `rgba(201,151,58,.22)` | `var(--flash)` (themed) |
| `@media(max-width:600px)` | — | carried over; `.qn` font-size and `.qi` padding-left re-tuned for the new mono/left-border treatment |

### 4. One markup change (outside the `<style>` block)
The search-icon SVG had a hardcoded `stroke="white"`, which only worked because the header used to always be dark navy. Changed to `stroke="currentColor"` with color inherited from `.sw { color: var(--faint) }`, since the header background is now a light surface color by default.

### 5. Explicitly not implemented
**Category/topic tag styling** — the spec's tag component rule (mono font, sage-green fills, hover-to-solid) has no target in this codebase: the `Q` quote data is `{id, text}` only, with no tag/category field anywhere. No tagging UI was invented to avoid turning a styling pass into a functional rewrite. If topic tags are added to the data model later, apply the rule from the original prompt (quoted above) to that new markup.

### 6. Unchanged by design
- All search/filter/copy/link/go-to-#/hash-deep-link JS (`render()`, `cp()`, `cl()`, `goTo()`, `handleHash()`, the search debounce listener) — zero behavior changes, same ids/classes throughout.
- The pre-existing theme toggle mechanism (`initTheme()`/`toggleTheme()`, `#themeBtn`) — reused as-is; only the CSS it drives changed.

## Files touched

- `index.html` — `<head>` font links removed, `<style>` block rewritten (lines ~7-76 originally), one `stroke="white"` → `stroke="currentColor"` attribute fix.
- `tb_joshua_quotes.html` and all other files — untouched (gitignored local copy, out of scope).

## Reproducing this on another site

To bring a different static page onto GOSW Dawn:
1. Copy the palette/typography block verbatim from this doc's "Original request" section (or from `index.html`'s `:root`/`@media`/`[data-theme]` blocks directly) into the target page's stylesheet.
2. Remove any web-font `<link>` tags; point heading/lead-text rules at `--font-serif`, body/chrome at `--font-sans`, and labels/metadata at `--font-mono` (uppercase, `letter-spacing:.1em`).
3. Apply the component rules (quote/pull-quote cards, tags if the data model has them, header/nav, dividers, card/image radius+shadow) using the mapping table above as a template — match rules to the closest analogous element on that page rather than copying selector names literally.
4. If a light/dark toggle doesn't already exist, add one that sets `data-theme="dark"|"light"` on `:root` (or `<html>`) and persists via `localStorage`, mirroring `initTheme()`/`toggleTheme()` in `index.html`.
5. Verify: toggle dark mode, then force the opposite of the OS preference via the manual toggle to confirm the `[data-theme]` tier wins; check gold/green contrast against paper/surface in both modes.
