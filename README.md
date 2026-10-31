# Winterberg Agricultural High School Website

A static, multi-page website for Winterberg Agricultural High School, built for
WEDE5020 (Part 1: HTML structure, Part 2: CSS styling and responsiveness,
Part 3: JavaScript, SEO and forms).

## Project structure

```
Winterberg Website/
├── index.html               # Home (hero, stats, gallery with lightbox)
├── pages/
│   ├── about.html           # About Us (timeline accordion)
│   ├── programs.html        # Programs (tabs)
│   ├── products.html        # Products (filter, subscription form)
│   ├── enquiry.html         # Enquiry (FAQ accordion, AJAX enquiry form)
│   └── contact.html         # Contact (Leaflet map, email-compile form)
├── assets/
│   ├── css/style.css        # Single external stylesheet
│   ├── js/main.js           # All JavaScript (Part 3)
│   ├── js/search-index.js   # Generated index used by site search
│   ├── data/pricing.json    # Sample prices/availability fetched by AJAX
│   └── images/              # Crest and gallery images
├── tools/build_search_index.py  # Rebuilds the search index after you edit page text
├── robots.txt
├── sitemap.xml
├── README.md
└── CHANGELOG.md
```

## How to view the site

Serve the folder with a local server (e.g. VS Code "Live Server") so relative
links and the AJAX request resolve correctly. Opening `index.html` directly also
works; the AJAX forms then use built-in fallback data.

## Part 3 — Enhancing functionality and SEO

All behaviour lives in `assets/js/main.js` (plain JavaScript, no framework; each
feature only runs if its markup is on the page). Pages remain readable with
JavaScript switched off.

| Brief item | Implementation |
|---|---|
| Accordions | FAQ on `enquiry.html`, timeline on `about.html` (ARIA, arrow-key support) |
| Tabs | Curriculum / Duty Roster / Safety on `programs.html` (keyboard + deep links such as `programs.html#duty-roster`) |
| Modal / lightbox gallery | `<dialog>` lightbox on the home page: click to enlarge, arrow keys, Esc, backdrop click, Download image button (PNG) |
| Interactive map | Leaflet + OpenStreetMap on `contact.html` with marker, popup and directions link (plain-link fallback if it cannot load) |
| Animations and transitions | CSS transitions/keyframes plus JS scroll-reveal, animated counters, sticky-header shrink (disabled for `prefers-reduced-motion`) |
| DOM manipulation | Enquiry form shows/hides fields and toggles `required` by topic; produce filter pills; mobile menu; dynamic error messages and result cards |
| enquiry.html form | Admissions / produce / volunteer / sponsor. After validation, the response (availability, indicative cost) is built from `assets/data/pricing.json` |
| contact.html form | Name, email, phone, message type, subject, message. Validated data is compiled into an email addressed to `amandac@winagric.co.za` and opened through a `mailto:` link |
| Site search | Header **Search** button (also press `/` or Ctrl+K): live results across every page with highlighted matches, arrow keys + Enter, and `?q=term` links. Uses `assets/js/search-index.js`. After editing page text, run `python tools/build_search_index.py` to refresh it |
| Form elements | `input`, `select`, `textarea`, `date`, `number`, `tel`, `email` |
| Validation | HTML5 attributes (`required`, `type`, `minlength`, `maxlength`, `pattern`, `min`/`max`) plus JavaScript: email format, South African phone numbers, name characters, character counts, date range |
| Error handling | Inline messages per field (`role="alert"`, `aria-invalid`), summary message, focus moves to the first error |
| AJAX | `fetch()` loads `pricing.json` asynchronously and renders the result without reloading the page (enquiry and box subscription forms) |
| Form submission | Every form has an `action` attribute; JavaScript intercepts the submit |

### SEO
- **On-page:** unique `<title>` and meta description per page, one `<h1>` per page with logical `h2`/`h3`, canonical links, Open Graph tags, JSON-LD (`EducationalOrganization`, plus `FAQPage` on the enquiry page), descriptive image file names and alt text, breadcrumbs, internal links, mobile-friendly responsive layout.
- **URL structure:** short descriptive names (`pages/programs.html`, `pages/products.html`).
- **robots.txt** and **sitemap.xml** are in the site root.
- **Off-page (actions for the school, not code):** claim a Google Business Profile for the Fort Beaufort address, list the school in local and education directories, ask local farming bodies and the education department for links, and share the site on the school's social media.
- **Page speed:** font preconnect with `display=swap`, lazy-loaded gallery images with width/height set, `defer`red script, one CSS and one JS file, tiny SVG gallery images.
- **Security:** Content-Security-Policy meta tag (scripts only from the site and unpkg), Leaflet loaded with Subresource Integrity, referrer policy, `rel="noopener noreferrer"` on external links, user input is never inserted as HTML (`textContent` only), no secrets in code. GitHub Pages serves over HTTPS.

### Deployment
GitHub Pages: repository **Settings → Pages → Deploy from a branch → main / root**.
If the published address differs from
`https://siyahlumakepe15-debug.github.io/Winterberg-Website/`, update it in
`sitemap.xml`, `robots.txt` and the `canonical` / `og:url` tags.

### Replace before submitting
- `assets/data/pricing.json` holds **sample** fees, prices and places. Replace with the school's real figures.
- The six gallery images are illustrations. Swap in real photos and update the alt text.

## Part 2 focus (previous submission)

CSS only, in `assets/css/style.css`, split into numbered, commented sections
(reset and variables, typography, layout, colour, pseudo-classes, media queries).
The brief's colours (yellow / white / black) and sizes (school name 26px, titles
14px, body 12px) are kept as CSS variables at the top of the file.
`Avenir Next LT Pro` is replaced by Poppins with a Century Gothic fallback.

## Testing

- Tested in Chromium at 1366px and 390px widths: no console or Content-Security-Policy errors.
- Exercised: lightbox, tabs, accordions, filter pills, mobile menu, and all three forms with valid and invalid input.
- **TODO (add your own evidence):** W3C HTML/CSS validator results, a Lighthouse report, and screenshots in Firefox/Safari.

## References

- MDN Web Docs (2026) *HTML dialog element*. https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dialog
- MDN Web Docs (2026) *Using the Fetch API*. https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch
- W3C (2025) *WAI-ARIA Authoring Practices: Accordion and Tabs patterns*. https://www.w3.org/WAI/ARIA/apg/patterns/
- Leaflet (2025) *Leaflet 1.9.4 documentation*. https://leafletjs.com/reference.html
- OpenStreetMap contributors (2026) *OpenStreetMap*. https://www.openstreetmap.org/copyright
- Google (2026) *Search Central: SEO starter guide*. https://developers.google.com/search/docs/fundamentals/seo-starter-guide
- Nielsen Norman Group (2026) *10 usability heuristics for user interface design*. https://www.nngroup.com/articles/ten-usability-heuristics/
- MDN Web Docs (2026) *CSS: Cascading Style Sheets* and *Using media queries*. https://developer.mozilla.org/en-US/docs/Web/CSS

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).
