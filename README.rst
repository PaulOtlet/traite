#############
INTRODUCTION
#############

************************
Transcribing the Traité 
************************

Help to transcribe Otlet's "Traité" from PDF to a digital full-text edition.
No easily readable edition of his works is currently accessible online.
While more and more books and articles are published about the "visionary of the digital age", the original sources remain accessible only to those who are willing to download or browse a 200 MB PDF-file and understand French.

The first goal is to produce a digital edition of the "Traité de Documentation" in HTML and EPUB format.
The tool of choice is the Sphinx documentation generator. It uses reStructuredText files as input.

The current version of the reST version can be found at https://github.com/PaulOtlet/traite . 
The rendered version is at http://traite.czam.de .

To contribute to this effort just get a copy of the `PDF of University of Ghent <http://lib.ugent.be/fulltxt/RUG01/000/990/276/BIB-038A006_2006_0001_AC.pdf>`_, open a text editor and start correcting the mistakes of the OCR run according to the rules layed out below. 


About Paul Otlet
=================

http://en.wikipedia.org/wiki/Paul_Otlet


About the Traité
=================

 * Wikipedia.org: `Traité de Documentation <https://en.wikipedia.org/wiki/Trait%C3%A9_de_Documentation>`_
 * Archive.org: https://archive.org/details/OtletTraitDocumentationUgent
 * OpenLibrary.org: https://openlibrary.org/works/OL1112871W/Traite%CC%81_de_documentation
 * Gent University
 
     * http://search.ugent.be/meercat/x/view/rug01/000990276 
     * http://lib.ugent.be/fulltxt/handle/1854/5612/
     * http://lib.ugent.be/catalog/rug01:000990276
     * http://buck.ugent.be/fulltxt/RUG01/000/990/276/BIB-038A006_2006_0001_AC.pdf
     
 * https://www.google.co.in/search?tbo=p&tbm=bks&q=inauthor:%22Paul+Otlet%22


https://archive.org/stream/OtletTraitDocumentationUgent/OtletTraitDocumentationUgent_djvu.txt  compared against FineReader 12 on 2014-04-05, FineReader was remarkably better.
Seems that the text version on Archive.org was updated in the meantime. 

Link to / show individual pages: https://archive.org/stream/OtletTraitDocumentationUgent#page/n24/mode/1up  is page 22.  but 179/180 are doubled


Crowd sourcing for proofreading and translation
================================================

 * http://wikisource.org
 * http://traduwiki.org/
 * https://www.transifex.com/
 * http://crowdin.net/pricing
 * https://poeditor.com/
 * http://www.hasecke.eu/Members/juh/sphinx-a-tool-for-self-publisher
 * https://www.discovermeteor.com/blog/community-translations-with-github-middleman-codeship-heroku/
 * http://annotatedbooksonline.com
 
Translation:

 * https://translate.google.com/
 * http://translation.babylon.com/french/to-english/

 
****************************
Sphinx and reStructuredText
****************************

The digital versions of the *Traité* are generated automatically 
by the `Sphinx <http://sphinx-doc.org>`_ documentation generator. 
Source files are written in 
`reStructuredText <https://en.wikipedia.org/wiki/ReStructuredText>`_ format.

An overview of the reST syntax can be found at http://sphinx-doc.org/rest.html .  

In the source files the `headings <http://sphinx-doc.org/rest.html#sections>`_
need to be marked up in a specific way.
We follow the `convention <https://docs.python.org/devguide/documenting.html#sections>`_ 
which is used for the Python programming language.

 - # with overline, for parts and languages TdD 
 - * with overline, for chapters 1-5
 - =, for sections  two-digit  11
 - -, for subsections  three-digit 111
 - ^, for subsubsections  111.1
 - ", for paragraphs   111.11
 - ., for 111.111
 

 - To compile: make html
 - To open the result
 
    - Linux: xdg-open _build/html/index.html
    - Windows: start _build\html\index.html
    - Mac: ?

To use the `Sphinx theme of ReadTheDocs <https://github.com/snide/sphinx_rtd_theme>`_ 
locally just install it by::

    pip install sphinx_rtd_theme

To avoid auto-enumerated lists when a paragraph starts with a number, 
the number needs to be escaped by a backslash ``\1. bla bla ...``    


Page layout
============

Pages should be structured like this::

    ====

    *<pg-nr>*　CHAPTER TITLE　<section-nr>  (can be mirrored, depending on even/odd page)
    
    ... texttext texttext texttext texttext texttext
    Before and after the chapter and section titles, 
    insert a unicode "wide space", copy-paste from "　", or U+3000 
    
    Line breaks should be placed as in the
    original text, including hyphenation. 
    For more details on hyphenation, see below...
    
    Paragraphs are separated by a blank line.
    ... texttext texttext texttext texttext texttext ...
    After the first column (and optional footnotes) put at least one
    blank line and then a horizontal bar ("----"):

    ----
    
    next column texttext texttext texttext texttext texttext texttext
    texttext texttext texttext texttext texttext texttext texttext texttext
    text texttext texttext texttext texttext texttext
    
    
    ====
    
    <section-nr>　CHAPTER TITLE *<pg-nr>*
    
    next page text ...
    text ...
    

In detail:

 - Pages are separated by horizontal rules "====" surrounded by
   two empty lines above and one blank line below the rule.
 - After a single blank line, page numbers, section/chapter titles and 
   section numbers should be placed just as in the PDF, 
   pages in *italics* (surrounded by ``*`` asterisks.)
 - The two columns on each page are separated by "----" surrounded by 
   two single blank lines.
 - Header markup should be one symbol longer than the header text
 - Unicode characters should be used wherever possible, but 
   should be documented somewhere
 - The original text, layout and typesetting should be represented as 
   close as possible within the limits of the reStructuredText format.
 - Hyphenation: What is a good solution to somehow mark a hyphenation 
   from the book in the reST format without it showing up in the compiled html?
   Leaving hyphenation in the reST would destroy full-text search.
   But single dashes (``-``) at the end of the line are easy 
   to remove with a script.
   Soft-hyphens can be used to replace the hyphenation so 
   that it doesn't show up in the browser. An open question is how 
   this will affect the epub output of Sphinx.
 - If the PDF resolution is not good enough to discriminate symbols
   accurately, just place three bold question marks **???** (surround
   them with two asterisks ``**???**``) in this position.

 
Special characters
===================

see also: http://character-code.com/french-html-codes.php

« .. »  left and right angle quotes
 
―  Horizontal rule (use above footnotes)
 
– EN Dash

— EM Dash

see also: http://en.wikipedia.org/wiki/Dash


The source files are encoded in unicode format (UTF-8 without BOM).
To check the encoding on Windows, 
use the excellent http://notepad-plus-plus.org editor.

To input specific letters or symbols:

Ubuntu12: Shift+AltGr + ^ + e = ê

https://de.wikipedia.org/wiki/%C5%92 U+0152 OEvre Œ, Kleinbuchstabe œ U+0153

Multiplication sign: × (Unicode 215)


https://help.ubuntu.com/community/ComposeKey
Unicode composition: Another means to enter characters is to enter them as Unicode character number.

Press Shift+Ctrl+U, release U, enter the hexadecimal (0123456789abcdef) Unicode character code point, then release Shift+Ctrl. An underlined u followed by the number will be displayed as you type.

Alternatively, press (and release) Shift+Ctrl+U, then, while underlined u is displayed, enter the hexadecimal Unicode character code point followed by <Return>. 

http://en.wikipedia.org/wiki/Unicode_input

Windows: http://superuser.com/questions/47420/insert-unicode-characters-via-the-keyboard

