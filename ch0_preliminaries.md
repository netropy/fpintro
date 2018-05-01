## 0. Preliminaries: Writing Text

#### Inspect some file formats for text documents (like .html/.doc/.txt).

* MacOS: open TextEdit.app
```
    ->New ->...type something...
    ->Save .rtf/.html/.xml/.doc
    ->Format->Make Plain/Rich Text
    ->Save .txt
```
* <https://en.wikipedia.org/wiki/Text_editor>
* <https://en.wikipedia.org/wiki/Plain_text>, <https://en.wikipedia.org/wiki/Binary_file>, <https://en.wikipedia.org/wiki/Formatted_text>

___Notes:___

* Binary file formats for documents require "word processing" apps or "tools" for reading and for writing.
* Binary file formats make collaboration difficult.  Tools may not be available on all "operating systems", may costs money.
* A binary file format can fall out of fashion or become "unsupported", creating a problem for long-term archival of texts.
* Plain text files can be written using a simple "text editor", easily exchanged, and viewed on different systems.
* file formats of above excercise:
  - .doc is binary: `\320\317^Q\340\241\261^Z\341^@^@^@^@`
  - .rtf is plain text: `{\rtf1\ansi\ansicpg1252\cocoartf1561\cocoasubrtf400 ... this is a sample text}`
  - .xml is plain text: `<?xml version="1.0" encoding="UTF-8" standalone="yes"?>...</w:body></w:wordDocument>`
  - .html is plain text: `<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" ...><html>...</body></html>`  
* File formats are _languages_.

#### Write formatted text in plain-text "Markdown" and render in a browser.

How to write Markdown texts ("cheat sheets"):

* <https://enterprise.github.com/downloads/en/markdown-cheatsheet.pdf>
* <https://guides.github.com/features/mastering-markdown>

Further reading:

* <https://en.wikipedia.org/wiki/Lightweight_markup_language>
* <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>,
* <https://help.github.com/articles/basic-writing-and-formatting-syntax>, <https://help.github.com/articles/organizing-information-with-tables>, <https://help.github.com/articles/creating-and-highlighting-code-blocks>

How to render Markdown texts as HTML an view in a browser:

* <https://en.wikipedia.org/wiki/Shell_(computing)>, <https://en.wikipedia.org/wiki/Command-line_interface>, <https://en.wikipedia.org/wiki/Graphical_user_interface>
* run in shell
```
    $ pandoc -o topics.html topics.md
    $ pandoc topics.md -o topics.html
    $ pandoc topics.md > topics.html
```
* open generated .html in <https://en.wikipedia.org/wiki/Web_browser>

___Notes:___

* Markdown is a simple format for styled editing and is easy to read and to write.
* Markdown is widely used and has become the format of choice for "collaborative" editing.
* Markdown can be easily converted to HTML, which is the standard markup language for web pages and web applications.
* Pandoc is just one of many tools converting .md to .html.
