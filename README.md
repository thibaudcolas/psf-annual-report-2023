# [PSF 2023 annual report - as HTML](https://psf-2023-report-as-html.netlify.app/)

Conversion of the official [2023 PSF Annual Impact Report (PDF, 16MB)](https://www.python.org/psf/annual-report/2023/) to HTML.

## Why?

PDF documents have a lot of known, unsolvable accessibility issues.

## How

- [pdftoppm](https://linux.die.net/man/1/pdftoppm) to convert whole pages to images
- [pdfimages](https://www.xpdfreader.com/pdfimages-man.html) to extract images from the PDF
- [pdftohtml](https://www.xpdfreader.com/pdftohtml-man.html) to extract text content (including links) as HTML
- [screenshot-to-code](https://github.com/abi/screenshot-to-code) to convert PDF page images to Tailwind HTML/CSS

```bash
pdftoppm -png -r 150 PSF_Annual_report_2023_v1b.pdf psf
pdfimages -png PSF_Annual_report_2023_v1b.pdf images
pdftohtml -fmt png PSF_Annual_report_2023_v1b.pdf report.html
```

## Unoptimized result

With [ImageOptim](https://imageoptim.com/) only:

- 6.2MB transfer weight (5.9MB of images)
- Requires JS to work
