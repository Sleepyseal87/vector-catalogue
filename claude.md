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
- GitHub + Cloudflare Pages → vitaldecor.co.th
- [any other technical conventions]

## Working Conventions
- Always state assumptions before proceeding
- Prefer complete deliverables over partial drafts
- SKU naming convention: [whatever you decided]

## Constraints
- No Python. Use bash, node, or direct file writes only.