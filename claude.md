# Vitaldecor Project Context

## Business
- Bangkok-based specification lighting, B2B
- Targets: interior designers, lighting designers, hotel procurement
- English-only content (quality filter)

## Current Product Line
- VECTOR line, flagship: SABLE series
- 15-20 SKUs in launch catalogue

## Visual Identity
- Colors:     
    --red:          #C41E3A;
    --plum:         #3D2645;
    --midnight:     #1F2937;
    --black:        #1a1a1a;
    --white:        #FFFFFF;
    --grey-light:   #F5F5F5;
    --grey-mid:     #E8E8E8;
    --grey-dark:    #666666;
    --stock-green:  #4CAF50;

## Catalogue Page Format & Responsive Behavior

### Design Canvas
- Format: 1080x1350px portrait (4:5 ratio)
- Design at 72dpi screen resolution
- Product image: 1160x967px on dark background

### Responsive Scaling Rules
The pages must behave like a responsive IG post — same design, adapts to screen:

- **Desktop:** Scale to fit viewport HEIGHT. No vertical scroll. Use CSS transform/scale or vh units.
- **Mobile:** Scale to fit viewport WIDTH. No horizontal scroll. Maintain aspect ratio.
- **Breakpoint:** Mobile treatment below 768px width.
- **Approach:** CSS `transform: scale()` anchored to appropriate origin, not reflowing content.

### Font Size Reference (at 1080px canvas)
- Product name: 48–56px
- Descriptor / subtitle: 28–32px
- Specs: 24–28px
- Price: 36–40px
- SKU codes: 20–24px
- Footer / contact: 18–22px

### Device Target Priority
1. Mobile phones (primary — Line chat sharing)
2. Desktop (secondary — designer office review)
3. iPad Pro (tertiary)
4. iPad Mini — known minor gap issue, not a priority fix

### Distribution Context
Pages are shared as URLs via Line chat. Must load fast and look complete without pinching or horizontal scrolling on first open.


## Stack / Deployment
- Static HTML, no build step. GitHub (Sleepyseal87/vector-catalogue) + Cloudflare Pages
- Live: catalogue.vitaldecor.co.th (also vector-catalogue.pages.dev). Push to `main` deploys in ~1-2 min
- `catalogue.html` loads every page listed in `catalogue-manifest.js` (order = catalogue order)
- `_headers`: html/js/css revalidate (max-age=0), images cache 1 day. Cloudflare zone Browser Cache TTL is set to "Respect Existing Headers", so these apply
- Images cache for a day: when swapping an image, rename the file or bump a `?v=` on its <img> src (e.g. retro75-render.jpg?v=2)

## Data Source (MPL is the authority)
- Master Product List: C:devital-decor-quoteVITAL_MASTER_PRODUCT_LIST_*.xlsx (newest date wins; currently 260924)
- If a page disagrees with the MPL, the MPL wins
- Blank in MPL: show a dash (—), do not invent a value. Exception: Dimming & Control is not in the MPL and is left as written
- Rf / Rg / Application are not in the MPL either; left as written
- Read the xlsx without Python: unzip it, parse xl/sharedStrings.xml + xl/worksheets/sheetN.xml with node (sheet2 = FIXTURES, sheet4 = LINEARS)

## Adding / Editing a Product Page
- Copy the closest existing *-spec.html (all share assets/spec.css), then update the manifest, datafields.csv (or datafields-linear.csv) and add the render + diagram to assets/
- The specs table is tight on the fixed 1350px canvas: an extra row in a cell (or a wrapped SKU line) can push it past the footer. Render and check (headless Edge works: msedge --headless --screenshot --window-size=1080,1350)
- PDFs (e.g. "Sable 75 - Specifications.pdf") are generated outside the repo; regenerate after spec changes. Starling R45 PDF not yet made
- Line endings: CSVs, catalogue-manifest.js and claude.md are CRLF; spec HTML files are LF. Keep each file's existing endings

## Working Conventions
- Always state assumptions before proceeding
- Prefer complete deliverables over partial drafts
- SKU Order Code = MPL Product ID (e.g. DL-STARLINGR45-3W, WL-TEMPO40). Products with several wattage IDs list all (Sable 75: DL-SABLE75-12W / DL-SABLE75-15W). Old codes (DLRD71509 etc.) are retired
- Linear Model field = first half of the MPL product name, uppercase (e.g. IAM8-036-168B). 5 strip models: IAM8-036/072/105-168B (8mm), IA10-144/216-...B (10mm)

## Open Items
- Sable 45, Sable 125, Sable 75 Pinhole (DL-SABLE75X-10W), Starling 35: in MPL, no page yet (sable125 render/diagram already in assets)
- Starling R45 PDF not generated
- MPL has no Halo 12W or Tempo 1W; pages already corrected to MPL

## Constraints
- No Python. Use bash, node, or direct file writes only.
