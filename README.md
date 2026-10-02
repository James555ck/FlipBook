# FlipBook

A page-turning flipbook viewer. It ships with the Leavers Brochure 2026, and you can upload your own
PDF or page images.

## Files
- `index.html` - the page: layout, styles and all the flip, upload, zoom and download logic
- `pages.js` - the 10 Leavers brochure pages, base64-encoded as a `PAGES` array

The page-turning library ([page-flip](https://github.com/Nodlik/StPageFlip) 2.0.7) is loaded from the jsDelivr CDN.

## Run it
Open `index.html` in a browser, or serve the folder:

    npx serve .

## Features
- Front and back covers sit centred, then slide to a two-page spread as they open (single page on phones).
- Every page turns the same way (one constant speed). Turn with drag, scroll, the arrows or the left/right keys.
- **Upload**: a PDF (rendered with PDFium, so gradients match Chrome) or several JPG / PNG page images
  (ordered by file name). The page title is taken from the file name.
- **Zoom** (desktop): buttons, Ctrl + scroll / pinch, or `+` `-` `0`. Drag or scroll to pan while zoomed.
- **Download** (only inside claude.ai): saves a self-contained, view-only `.html` copy named after the title.
- Soft per-page shadows for contrast on the white background.

## Notes
- Uploaded pages are rendered to JPEGs in the browser (up to 80 pages, 2200 px on the long side).
- The Download button relies on the claude.ai artifact `downloads` capability, so it stays hidden elsewhere.
