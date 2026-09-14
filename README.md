# Easy Invoice

A single, self-contained HTML file for creating simple, printable invoices (Rechnungen) —
no build tools, no backend, no dependencies. Everything runs client-side in the browser.

🔗 **Live version:** https://petermue.github.io/easy-invoice

## Features

- **A4 / DIN 5008 print layout** — optimized for German window envelopes ("Fensterumschlag,
  Fenster links"). The recipient address is precisely positioned so it shows correctly through
  a standard DIN 5008 window envelope.
- **Click-to-edit** — every piece of content (sender, recipient, invoice number/dates, item
  rows, notes, footer/company details) is directly editable in the page itself
  (`contenteditable`). No config files, no JSON, no forms — just click on the text and type.
- **Dynamic item rows** — add or remove invoice line items with a button; totals (net, VAT,
  gross) are calculated automatically.
- **Privatrechnung-friendly** — supports invoices without VAT (e.g. §19 UStG Kleinunternehmer
  or private individuals not permitted to charge VAT). Set the tax rate to `0` and a single
  "Rechnungsbetrag" total is shown instead of a net/VAT breakdown. Optional fields
  (Kundennummer, Ansprechpartner, VAT/Steuernummer, company register info, etc.) automatically
  disappear from the printed page when left empty.
- **Print-only cleanup** — placeholder hints, empty optional fields/rows, and on-screen editing
  affordances (borders, hover highlights, add/remove buttons) are all automatically hidden when
  printing or exporting to PDF, so the printed result looks like a clean, professional invoice.
- **Bookmarkable state** — click "Aktuellen Stand als Link kopieren" to copy a URL that encodes
  the entire current invoice content (all fields and line items) as a Base64 payload in the
  query string. Save that link, share it, or reopen it later to restore the invoice exactly as
  it was — no server or storage required.
- **Footer always at the page bottom** — the footer (company/bank details) stays anchored to
  the bottom of the printed A4 page regardless of how much or how little content the invoice
  has.
- **Optional letterhead** — an optional company/person name plus a subline/slogan can be added
  at the very top of the page (e.g. for a personal or business "Briefkopf"). Left empty by
  default; hidden automatically when printed if unused.

## Usage

1. Open [`index.html`](index.html) directly in a browser (double-click the file, or visit
   the [live version](https://petermue.github.io/easy-invoice/index.html)).
2. Click on any text to edit it: sender/recipient address, invoice number & dates, greeting
   text, line items, tax rate, notes, and footer/company details.
3. Use **"+ Position hinzufügen"** to add invoice line items, and the **"×"** button on a row
   to remove it. Totals recalculate automatically.
4. Leave optional fields empty if you don't need them (e.g. Kundennummer, Ansprechpartner,
   USt-IdNr., Geschäftsführer, letterhead) — they will not appear in the printed/exported
   invoice.
5. When done, print via <kbd>Ctrl/Cmd</kbd> + <kbd>P</kbd> and choose "Save as PDF" or print
   directly. The layout is tuned for A4 paper.
6. Optional: click **"🔗 Aktuellen Stand als Link kopieren"** to copy a bookmark URL with your
   current invoice data baked in. Reopening that link (even after closing the browser)
   restores the exact same content, so you can keep a "template" link or share a draft.

> **Note on the bookmark feature:** the entire invoice content is encoded directly in the URL
> (Base64, UTF-8 safe). Nothing is uploaded or stored anywhere — the link only works because
> the data travels with it. Long invoices with many line items will produce a longer URL.

## DIN 5008 / window envelope compatibility

The recipient address block is positioned per DIN 5008 Form A conventions (address window
starting 45 mm from the top, 20 mm from the left, sized for a standard long window envelope
with the window on the left). If you use a different envelope standard, you may need to adjust
the `.address-window` positioning in the CSS.

## Privacy

All data stays in your browser. There is no backend, no analytics, no external requests, and no
data is transmitted anywhere except what you put into the bookmark URL yourself (see above).
This makes the tool suitable for offline use as well — just save `invoice.html` locally.

⚠️ **Be careful with sharing the bookmark URL.** The invoice data in the URL is only Base64-encoded,
not encrypted or protected in any way — anyone with the link can read the full invoice content
(names, addresses, amounts, bank details, etc.). Treat the link like the invoice document itself:
don't post it publicly, and only share it over channels you'd trust with the invoice's contents.

## Customization

Everything (colors, fonts, margins, default text) lives in a single file, `invoice.html`.
Look for the `<style>` block in the `<head>` for layout/design and the HTML body for default
placeholder content. No build step is required — just edit and reload.

## License

MIT License — feel free to use, modify, and share this template for your own invoicing needs.
See [LICENSE](LICENSE) for the full text.
