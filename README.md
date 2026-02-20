# Vitaldecor Sable 75 Catalogue Pages

Two HTML pages for the Sable 75 product catalogue:

## Files
- `sable75-mood.html` - Dark mood/hero page (1080x1350px)
- `sable75-spec.html` - Light specifications page (1080x1350px)

## How to Use

### 1. View in Browser
Open either HTML file in Chrome/Firefox/Safari to see the layout.

### 2. Replace Mood Photo
In `sable75-mood.html`, find line ~36:
```html
background: url('MOOD_PHOTO_PATH_HERE.jpg') center center no-repeat;
```
Replace `MOOD_PHOTO_PATH_HERE.jpg` with your dramatic hotel lobby photo path.

### 3. Replace Product Images
In `sable75-spec.html`:
- Product render: Replace placeholder div around line 175
- Technical diagram: Replace placeholder div around line 182

### 4. Export as PNG

**Option A: Browser Screenshot**
1. Open HTML in Chrome
2. Press F12 (DevTools)
3. Press Ctrl+Shift+P (Command Palette)
4. Type "screenshot" → Select "Capture full size screenshot"
5. Saves as PNG

**Option B: Online Tool**
1. Upload HTML to https://html2canvas.hertzen.com/
2. Or use https://www.web2pdfconvert.com/

**Option C: MacOS/Linux Command Line**
```bash
# Using wkhtmltoimage
wkhtmltoimage --width 1080 --height 1350 sable75-mood.html sable75-mood.png
wkhtmltoimage --width 1080 --height 1350 sable75-spec.html sable75-spec.png
```

## Customization

### Colors
- Brass/Gold: `#B8860B`
- Dark Charcoal: `#2B2B2B`
- Wine Purple: `#4A1E2C`
- Light Grey: `#E8E8E8`

### Fonts
Currently using system fonts (Arial/Helvetica). To use custom fonts:
```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap');
font-family: 'Outfit', sans-serif;
```

### Dimensions
Pages are 1080x1350px (Instagram portrait format).
To change: Edit `width` and `height` in `<meta viewport>` and `<body>` CSS.

## Template Structure

### Mood Page (Dark)
- Hero image (full bleed)
- Overlay gradient for text legibility
- Product name + tagline (bottom left)
- Logo + contact (bottom footer)

### Spec Page (Light)
- Product name + tagline (top)
- Product images side-by-side
- Application context
- Performance specs
- 3 specification tables
- Pricing + SKU + stock status
- Logo + contact footer

## Next Steps
1. Add your mood photo to mood page
2. Add product render + diagram to spec page
3. Export as PNG (1080x1350px)
4. Use for Line sharing, IG posts, PDF catalogue
5. Duplicate and modify for other SKUs

---

**Need changes?** Edit the HTML directly. CSS is inline in `<style>` tags.
