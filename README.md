---
title:      "README"
subtitle:   "docbook52pdf - universal markup to pdf converter"
author:     "Jens Getreu"
date:       "2020-04-01"
lang:       "en_GB.UTF-8"
---

# Docbook 5 to Pdf

_docbook52pdf_ is an universal _markup-language to pdf_ converter.
It comes as small Bash-script that combines different products to a 
rendering-tool-chain. 


## How it works

1. The script uses `pandoc` to convert: _commonmark, creole, csv, docbook,
   docx, dokuwiki, epub, fb2, gfm, haddock, html, ipynb, jats, jira, json,
   latex, man, markdown, markdown_github, markdown_mmd, markdown_phpextra,
   markdown_strict, mediawiki, muse, native, odt, opml, org, rst, t2t, textile,
   tikiwiki, twiki_ and _vimwiki_ into Docbook 5.

   In case the input is available as Docbook 5 _xml_-file, this stage is
   skipped.

2. The resulting Docbook 5 is validated with `xmlstarlet` and converted into
   formatting objects with `xsltproc`. The styles are based on
   `asciidoctor-fopub`.

3. The final _pdf_-file is generated with Apache `fop`.


## Installation and usage

1. Install dependencies:

       sudo apt install pandoc docbook5-xml docbook-xsl-ns xsltproc fop xmlto libxml2-utils xmlstarlet

2. Download the template:

       git clone git@github.com:getreu/docbook52pdf.git

3. Copy and rename the template directory:

       cp -r docbook52pdf/template .
       mv template my_document

4. Edit the template:

       vi my_document/source/main.md

5. Render:

       ./my_document/make

   This generates the file `./my_document/build/pdf/main.pdf`.
