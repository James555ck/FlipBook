# Leavers 2027 FlipBook

A page-turning flipbook viewer. It ships with the Leavers 2027 brochure, and visitors can upload their own
PDF or page images.

**Live page (GitHub Pages):** https://james555ck.github.io/FlipBook/

## Files
- `index.html` - the page: layout, styles and all the flip, upload, zoom and download logic
- `pages.js` - the 10 brochure pages, base64-encoded as a `PAGES` array

The page-turning library ([page-flip](https://github.com/Nodlik/StPageFlip) 2.0.7) loads from the jsDelivr CDN.

## Run it locally
Open `index.html` in a browser, or serve the folder:

    python -m http.server 8080

then visit http://localhost:8080

## Publish with GitHub Pages
1. Make the repository public (Settings > General > Danger Zone > Change visibility).
2. Settings > Pages > Build and deployment > Source: **Deploy from a branch**, Branch: **main** / **(root)** > Save.
3. After a minute the site is live at https://james555ck.github.io/FlipBook/

## Features
- Front and back covers sit centred, then slide to a two-page spread as they open (single page on phones).
- Every page turns the same way at one constant speed. Turn with drag, scroll, the arrows or the left/right keys.
- **Upload**: a PDF (rendered with PDFium, so gradients match Chrome) or several JPG / PNG page images
  (ordered by file name). The page title comes from the file name.
- **Zoom** (desktop): buttons, Ctrl + scroll / pinch, or `+` `-` `0`. Drag or scroll to pan while zoomed.
- **Download PDF**: one PDF page per flipbook page, named after the title.
- **Download Flipbook**: a single self-contained, view-only `.html` file (no upload), named after the title.
- Soft per-page shadows for contrast on the white background.

## Notes
- Uploads are processed entirely in the visitor's browser (up to 80 pages, 2200 px on the long side); nothing is sent to a server.
- Uploading a PDF needs an internet connection the first time, because the PDF engine loads from a CDN.
