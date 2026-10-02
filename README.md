# Leavers 2027 FlipBook

A page-turning flipbook for the Leavers 2027 brochure. Customers download the Word version, add their own
details, upload it, and get a PDF and a digital flipbook they can share.

**Live page (GitHub Pages):** https://james555ck.github.io/FlipBook/

## How customers use it
1. **Customise your Leavers 2027 brochure** - type the company details, choose a logo and press **Update flipbook**.
   The page fills the Word template's placeholder lines and both logo boxes and redraws the brochure.
2. **Download** - **Download PDF** (true A4), **Download digital flipbook** (one self-contained, view-only `.html` file to share)
   and **Download leavers designs** (the six EPS design files in one zip).

PDF and flipbook unlock once the flipbook has been updated. The designs download is always available.

## Files
- `index.html` - the page: layout, styles and all the flip, upload, zoom and download logic
- `pages.js` - the 10 template pages (base64 images) shown before anything is uploaded
- `Leavers-2027-designs.zip` - the EPS design files that **Download leavers designs** saves (replace the zip to change them)
- `Leavers-2027.docx` - the Word template the page fills in (its placeholder lines and logo boxes). Replace it to change the design

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
Replace `Leavers-2027.docx` with the new Word file. The placeholders the form fills are the text lines `[Your company Name]`,
`[Address line 1]`, `[Town]`, `[Postcode]`, `[Phone]` and `[Website]`, and the picture controls tagged `LogoFront` / `LogoBack`.
The pictures shown before anything is customised are in `pages.js` (the template's pages as drawn by the page itself).

## Other features
- Front and back covers sit centred, then slide to a two-page spread as they open (single page on phones).
- Every page turns the same way at one constant speed. Turn with drag, scroll, the arrows or the left/right keys.
- The file upload (PDF, Word, images) is still in the code but switched off in the page.
- **Zoom** (desktop): buttons, Ctrl + scroll / pinch, or `+` `-` `0`. Drag or scroll to pan while zoomed.
- Soft per-page shadows for contrast on the white background.
- **PDF quality:** for Word templates the PDF keeps each page's own picture exactly as stored in the Word file (no re-compression)
  and draws the logo and text as a separate sharp layer, on true A4 pages.

## Notes
- Uploads are processed entirely in the visitor's browser (up to 80 pages, 2200 px on the long side); nothing is sent to a server.
- PDF and Word upload load their helper libraries from a CDN, so they need an internet connection the first time.
- Downloaded flipbooks are view-only (no upload, no template).
