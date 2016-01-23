PageNumberPrefixes
==================

This is a revision to a customization layer for the DocBook XSL Stylesheets to
support page number prefixes. e.g. chapter numbers. The original version is
located at:

    http://wiki.docbook.org/PageNumberPrefixes
    
This version has been modified to work with the 1.78.1 version of the Docbook
XSL Stylesheets. The previous version was based on the 1.60.1 version.

Usage
-----

You should be able to copy the contents of the stylesheet (below) into an XSL
file and import it into your own customization layer. The templates this
stylesheet customizes are:

  - name="toc.line" -- put page number prefixes in the TOC
  - match="indexterm" mode="reference" -- put page number prefixes in the Index
  - name="reference" -- put page number prefixes in the Index
  - match="indexterm" mode="reference-markup" -- put page number prefixes in the Index
  - match="reference-markup" -- put page number prefixes in the Index
  - name="footer.content" -- put page number prefixes on each page
  - match="chapter" -- Restart page numbering at chapters
  - match="book/index|part/index" -- Restart page numbering at Index 

This customization also adds an extra mode: page-number-prefix. In the templates
that put in an &lt;fo:page-number-citation/&gt;, the customizations just call this
mode. The default template for this mode (match="*") does nothing. The
customization has templates that match on elements or their descendants to
specify a prefix.

If you use appendix, bibliography, or glossary in your documents, you will
probably want to do some additional customizations so the page numbering
restarts at these elements, also. (Add initial-page-number="1" to the
&lt;fo:page-sequence/&gt; created for these elements. See the templates matching
chapter and index for examples.) You may also want to do something different
with references, parts, and refentry's than this customization currently does.
(For the ANSYS documentation, the page-number-prefix for these elements comes
from the chapter preceding the reference material.)

