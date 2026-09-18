My Website
Added css
Made some changes for index
A static, multi-page website for Winterberg Agricultural High School, built for
WEDE5020 (Part 1: HTML structure, Part 2: CSS styling and responsiveness).

## Project structure

```
Winterberg Website/
├── index.html               # Home page
├── pages/
│   ├── about.html            # About Us page
│   └── contact.html          # Contact Us page (contact details, map, enquiry form)
├── assets/
│   ├── css/
│   │   └── styles.css        # Single external stylesheet, linked from every page
│   ├── images/                # Site images
│   └── js/                    # Reserved for future JavaScript (Part 3)
├── README.md
└── CHANGELOG.md
```

## How to view the site

Open `index.html` in a browser, or serve the folder with a local server
(e.g. VS Code "Live Server" extension) so relative links resolve correctly.

## Part 2 focus (this submission)

Part 2 of the POE covers CSS only — no new HTML content or JavaScript was
added beyond what was needed to make Part 1's markup valid and stylable.
Everything below lives in **`assets/css/styles.css`**, split into numbered
sections with comments:

| Checklist item | Where it lives |
|---|---|
| External stylesheet, linked on every page | `<link rel="stylesheet" href=".../styles.css">` in the `<head>` of all 3 pages |
| Default CSS styles | Section 1 — reset, `:root` variables, base `body`/`a`/`img` rules |
| Typography | Section 2 — school name, page titles and body copy sizes, using `rem` |
| Layout structure | Section 3 — header/nav, hero grid, card grid, footer |
| Decoration & colour | Section 4 — the yellow / white / black brand palette, cards, buttons |
| Pseudo-classes | Section 5 — `:hover`, `:focus`, `:active`, `:visited`, `:first-child`, `:last-child`, `:nth-child()`, `:required`, `:invalid`, `:checked`, `:disabled` |
| Media queries / breakpoints | Section 9 — 480px, 768px and 1024px breakpoints |
| Responsive layout | `.hero` and `.card-group` switch from stacked (mobile) to grid columns (tablet/desktop) |
| Responsive typography | `rem`-based font variables that scale up at each breakpoint (mobile-first) |
| Responsive navigation | Pure-CSS checkbox "hamburger" menu below 768px |
| Responsive images | `img { max-width: 100%; height: auto; }` |

## Design decisions / assumptions

- The business brief specifies the school name at 26px, page titles at 14px
  and body copy at 12px. Those exact values are used as the **mobile**
  baseline, and scaled up with `rem`-based custom properties at the tablet
  and desktop breakpoints — this satisfies both "apply the brand typography"
  and "responsive typography" in one system.
- `Avenir Next LT Pro` is a licensed font and isn't guaranteed to be
  installed on a visitor's device, so the `font-family` stack falls back to
  `Century Gothic`, then a system sans-serif, to keep the same geometric feel.
- Colour palette: `#f5c400` (yellow), `#1a1a1a` (near-black), `#ffffff`
  (white), plus a light grey (`#f4f4f2`) used only for alternating section
  backgrounds — kept close to the "Yellow, White, Black" brief.

## Testing

<!-- TODO: add your own testing evidence here, e.g.:
- Tested in Chrome, Firefox and Safari at 375px, 768px and 1440px widths.
- Validated HTML with the W3C validator and CSS with the (Jigsaw) CSS validator.
- Checked contact form required fields and email input type.
Attach or link screenshots/recordings as your lecturer requires. -->

## References

- Nielsen Norman Group (2026) *10 usability heuristics for user interface
  design*. Available at: https://www.nngroup.com/articles/ten-usability-heuristics/
  (Accessed: 5 August 2026).
- MDN Web Docs (2026) *CSS: Cascading Style Sheets*. Available at:
  https://developer.mozilla.org/en-US/docs/Web/CSS (Accessed: 18 September 2026).
- MDN Web Docs (2026) *Using media queries*. Available at:
  https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries
  (Accessed: 18 September 2026).
<!-- Add any further sources you used while building the CSS. -->

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for the full list of changes, including
what was fixed in response to Part 1 feedback.
