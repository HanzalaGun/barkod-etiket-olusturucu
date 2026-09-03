[Türkçe](README.md) · **English** · [Русский](README.ru.md) · [Deutsch](README.de.md) · [العربية](README.ar.md)

# Barcode label maker

Turns a product list into printable barcode labels. A single `index.html` file —
no install, no build step, no server. Double-click and it opens.

**Live version:** [hanzala.com.tr/araclar/barkod-etiket-olusturucu](https://hanzala.com.tr/araclar/barkod-etiket-olusturucu)

<br>

## What it does

- **EAN-13 and Code 128.** Give EAN-13 twelve digits and it works out the check
  digit for you; give it thirteen with a wrong one and it says so rather than
  quietly printing a broken barcode.
- **A4 label sheets** (70×37, 105×37, 52.5×29.7, 38×21, 105×74 mm) or a custom
  mm size for a **thermal label printer**. In roll mode each label gets its own
  page.
- **Quantity column** — how many labels of the same product to print.
- **Old price column** — struck-through old price with the discount percentage.
- Four layouts, text scale, bold/italic, hiding the name or the price.

Nothing is sent anywhere: the list you type never leaves the browser, there is
no server.

<br>

## Input format

One product per line, columns separated by a **tab**, **semicolon** or **pipe**:

```
Ground coffee	8690000000012	45	2
Tea	869000000002	20
Tea on offer	8690000000012	20	1	35
```

`name · barcode · price · quantity · old price` — a blank quantity counts as 1.

If a line has none of those three separators, it falls back to the comma. The
comma is deliberately the last resort: Turkish prices are written `145,90`, and
treating the comma as a separator made the price 145 and the quantity 90 — the
user asked for one label and got ninety.

<br>

## Languages

Turkish, English, Russian, German and Arabic — the same set the website uses.
The measurements, the sample list, the sheet names and the warnings are
translated too: `52,5×29,7 mm` becomes `52,5×29,7 мм` in Russian and
`52.5×29.7 mm` in English.

Arabic is laid out right to left, with two exceptions: the product list box
stays left to right and left-aligned (people paste this list out of a
spreadsheet, so the columns have to stay in the order they were pasted), and so
does the label preview — that box is print output and must not follow the page
direction.

Each language has its own address: `index.html?dil=en`. Share the link and it
opens in the same language; the `hreflang` tags point at those addresses too.
With no language chosen the browser's own language is used, and Turkish if that
is not one of the five.

The sample list only changes with the language while you have not typed anything
yourself — switching language never wipes a list you wrote.

<br>

## Using it

Download `index.html` and double-click it. Barcode drawing uses
[JsBarcode](https://github.com/lindell/JsBarcode) over a CDN, so the first load
needs an internet connection.

To put it on your own site, copy the file as it is; it has no other dependency.

<br>

## Self-check

Open `index.html?test=1`. Checks run for the check-digit arithmetic, separator
selection and barcode validation; then every language's translation table is
checked for missing keys and layout names. If one fails, the tab title becomes
`HATA:`.

<br>

## Licence

MIT — [LICENSE](LICENSE). Use it, change it, sell it.

This tool was written for [hanzala.com.tr](https://hanzala.com.tr), where there
are [more free tools](https://hanzala.com.tr/araclar) too.
