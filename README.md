# Leavers 2027 FlipBook

A page-turning flipbook for the Leavers 2027 brochure. Customers download the Word version, add their own
details, upload it, and get a PDF and a digital flipbook they can share.

**Live page (GitHub Pages):** https://james555ck.github.io/FlipBook/

## How customers use it
1. **Download to customise** - saves `Leavers 2027.docx`. Open it in Word, add your company details on the back page
   (the six white placeholder lines), drop in any images you need, then save it.
2. **Upload your .docx** - drop the saved file on the page (or use the button). It appears in the flipbook so you can check it.
3. **Download PDF** (the brochure as a PDF) and **Download digital flipbook** (one self-contained, view-only `.html` file to share).

Step 3 unlocks once a file has been uploaded.

## Files
- `index.html` - the page: layout, styles and all the flip, upload, zoom and download logic
- `pages.js` - the 10 brochure pages (base64 images) shown before anything is uploaded
- `template.js` - the Word template that **Download to customise** saves (base64 of `Leavers 2027.docx`)

The page-turning library ([page-flip](https://github.com/Nodlik/StPageFlip) 2.0.7) loads from the jsDelivr CDN.

## Run it locally
Open `index.html` in a browser, or serve the folder:

    python -m http.server 8080

then visit http://localhost:8080

## Publish with GitHub Pages
1. Make the repository public (Settings > General > Danger Zone > Change visibility).
2. Settings > Pages > Build and deployment > Source: **Deploy from a branch**, Branch: **main** / **(root)** > Save.
3. After a minute the site is live at https://james555ck.github.io/FlipBook/

## Updating the Word template
Replace the template by regenerating `template.js`:

    node -e "const fs=require('fs');fs.writeFileSync('template.js','const TEMPLATE_DOCX = \"'+fs.readFileSync('Leavers 2027.docx').toString('base64')+'\";\n')"

The upload reader expects a brochure-style Word file: one full-page picture per page, with any text in text frames
or boxes placed on top of the pictures. Pictures and text you add are drawn where Word shows them.

## Other features
- Front and back covers sit centred, then slide to a two-page spread as they open (single page on phones).
- Every page turns the same way at one constant speed. Turn with drag, scroll, the arrows or the left/right keys.
- Upload also accepts a PDF (rendered with PDFium) or several JPG / PNG page images; ordinary text-only Word
  documents are converted to simple A4 landscape pages.
- **Zoom** (desktop): buttons, Ctrl + scroll / pinch, or `+` `-` `0`. Drag or scroll to pan while zoomed.
- Soft per-page shadows for contrast on the white background.

## Notes
- Uploads are processed entirely in the visitor's browser (up to 80 pages, 2200 px on the long side); nothing is sent to a server.
- PDF and Word upload load their helper libraries from a CDN, so they need an internet connection the first time.
- Downloaded flipbooks are view-only (no upload, no template).
