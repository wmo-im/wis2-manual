# WIS2 Manual

## Overview

This directory manages the WIS2 Manual.  This document is designed to ensure that the data,
information and communication practices, procedures and specifications that WMO Members
employ in the operation of the WMO Information System (WIS) are adequately uniform and standard.

### Dependencies

Documentation is managed with [Asciidoctor](https://asciidoctor.org).

Link checking is managed with [asciidoc-link-check](https://www.npmjs.com/package/asciidoc-link-check).

PDF generation is managed with [asciidoctor-pdf](https://www.npmjs.com/package/asciidoctor-pdf).

```bash
apt-get install pandoc
npm install asciidoctor asciidoctor-pdf asciidoc-link-check
```

### Building the document

```bash
# create HTML (single page)
asciidoctor --trace -o wis2-manual.html index.adoc
# create PDF
asciidoctor --trace -r asciidoctor-pdf --trace -b pdf -o wis2-manual.pdf index.adoc
# create Word document
asciidoctor --trace --backend docbook --out-file - index.adoc | pandoc --from docbook --to docx --output wis2-manual.docx
```

# check links
```bash
find . -name "???.adoc" -exec asciidoc-link-check -p -c asciidoc-link-check-config.json {} \;
```

**Note**: `Makefile` provides shortcuts to these commands if you are able to run `make`.
