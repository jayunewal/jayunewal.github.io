# jayunewal.github.io

Portfolio site of Jay Unewal. Live at https://jayunewal.com

Plain static HTML, no build step. GitHub Pages serves the `main` branch root.

| File | What it is |
|---|---|
| `index.html` | Landing page |
| `resume.html` | Full resume (has its own print styles) |
| `Jay-Unewal-Resume.pdf` | Resume PDF, generated from `resume.html` |
| `404.html` | "Sheet not found" page for broken links |
| `img/` | Photo of Jay (480 and 800px wide, WebP and JPEG) |
| `og-image.png` | 1200x630 link-preview card (LinkedIn, WhatsApp, Slack) |
| `favicon.svg`, `favicon.ico`, `apple-touch-icon.png` | Icons |
| `fonts/` | Self-hosted Archivo and Martian Mono, cut down to what the pages use (OFL, see `fonts/OFL.txt`) |
| `robots.txt`, `sitemap.xml`, `CNAME` | Crawlers and custom domain |

## When you change things

- **Resume text changed:** regenerate the PDF so it matches. Open `resume.html` in Chrome, Print, Save as PDF, A4, "Background graphics" on, and save over `Jay-Unewal-Resume.pdf`.
- **Preview card changed:** give the new image a new file name (for example `og-image-2.png`) and update the `og:image` tags, so LinkedIn refreshes its cache. Then paste the URL into https://www.linkedin.com/post-inspector/.
- **New characters that the fonts don't have** (the fonts keep only characters used on the pages): rebuild from the full Google Fonts files with fontTools:

  ```sh
  fonttools varLib.instancer Archivo[wdth,wght].ttf wght=300:850 wdth=72:125 -o a.ttf
  fonttools varLib.instancer MartianMono[wdth,wght].ttf wght=400:800 wdth=75:87.5:87.5 -o m.ttf
  pyftsubset a.ttf --unicodes-file=chars.txt --flavor=woff2 --layout-features='*' --output-file=fonts/archivo.woff2
  pyftsubset m.ttf --unicodes-file=chars.txt --flavor=woff2 --layout-features='*' --output-file=fonts/martian.woff2
  ```

  `chars.txt` lists U+ codes for printable ASCII plus every other character in the three HTML files.
