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

## File size results

### Unoptimized

With [ImageOptim](https://imageoptim.com/) only:

- 6.2MB transfer weight (5.9MB of images)
- Requires JS to work

### Optimized

Sample commands:

```bash
avifenc --min 20 --max 30 25-2023-expenses-by-category.png 25-2023-expenses-by-category.avif
pngquant -f --quality=70-80 25-2023-expenses-by-category.png -o 25-2023-expenses-by-category-n.png
avifenc --min 20 --max 30 report-2_1.jpg report-2_1.avif
cjpegli -q 70 report-2_1.jpg report-2_1-li.jpg
```

Result:

| File                                         | Original size (KB) | Jpegli / pngquant (KB) | AVIF (KB) |
| -------------------------------------------- | ------------------ | ---------------------- | --------- |
| 25-2023-expenses-by-category.png             | 56                 | 16                     | 16        |
| 25-psf-asset-trends-from-2018-2023.png       | 40                 | 12                     | 12        |
| 26-psf-grant-disbursement-from-2016-2023.png | 80                 | 28                     | 24        |
| 26-psf-grant-trends-from-2016-2023.png       | 48                 | 16                     | 12        |
| 27-psf-grants-by-continent.png               | 152                | 44                     | 32        |
| report-10_1.jpg                              | 40                 | 16                     | 16        |
| report-10_2.jpg                              | 120                | 44                     | 32        |
| report-10_3.jpg                              | 100                | 36                     | 28        |
| report-11_1.jpg                              | 28                 | 12                     | 12        |
| report-11_2.jpg                              | 212                | 132                    | 76        |
| report-11_3.jpg                              | 124                | 36                     | 20        |
| report-12_1.jpg                              | 68                 | 28                     | 20        |
| report-13_1.jpg                              | 328                | 112                    | 56        |
| report-14_1.jpg                              | 76                 | 32                     | 28        |
| report-15_1.jpg                              | 132                | 56                     | 48        |
| report-17_1.jpg                              | 108                | 40                     | 28        |
| report-17_2.jpg                              | 164                | 64                     | 52        |
| report-18_1.jpg                              | 288                | 76                     | 32        |
| report-19_2.jpg                              | 104                | 40                     | 40        |
| report-19_3.jpg                              | 92                 | 36                     | 32        |
| report-19_4.jpg                              | 172                | 136                    | 60        |
| report-19_5.jpg                              | 96                 | 40                     | 28        |
| report-20_1.jpg                              | 72                 | 24                     | 16        |
| report-20_2.jpg                              | 248                | 92                     | 64        |
| report-20_3.jpg                              | 108                | 44                     | 28        |
| report-22_1.jpg                              | 156                | 64                     | 60        |
| report-22_2.jpg                              | 112                | 48                     | 44        |
| report-22_3.jpg                              | 144                | 60                     | 56        |
| report-28_1.jpg                              | 188                | 132                    | 60        |
| report-28_2.jpg                              | 196                | 136                    | 68        |
| report-2_1.jpg                               | 188                | 132                    | 40        |
| report-4_1.jpg                               | 116                | 40                     | 40        |
| report-4_2.jpg                               | 108                | 40                     | 36        |
| report-5_1.jpg                               | 104                | 40                     | 24        |
| report-5_2.jpg                               | 176                | 128                    | 60        |
| report-7_1.jpg                               | 196                | 132                    | 48        |
| report-8_1.jpg                               | 48                 | 16                     | 16        |
| report-9_1.jpg                               | 128                | 52                     | 40        |
| report-9_2.jpg                               | 196                | 136                    | 64        |
| report-9_3.jpg                               | 104                | 40                     | 44        |
| report-9_4.jpg                               | 152                | 60                     | 52        |
| report-9_5.jpg                               | 84                 | 28                     | 16        |
| report-9_6.jpg                               | 104                | 36                     | 36        |
| Total                                        | 5556               | 2532                   | 1616      |
