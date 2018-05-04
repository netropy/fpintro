## 0. Preliminaries: Writing Text, the Markdown Language, the Scala and Clojure Language Shells (REPL)

Here, the bare minimum of what one needs to know:

* how to write a text document like this one
* how to run Clojure and Scala code for the exercises.

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
* file formats of above exercise:
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

#### Install Clojure, Scala and run the language shells (REPL)

___TODO:___ link to install Scala, Leiningen

A _language shell_ or [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) reads (typically small) chunks of programming code as text input, then directly executes (evaluates) it, and prints the result as text output.  

To run the Scala shell:
```
    $ scala
    Welcome to Scala 2.12.5 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_172).
    Type in expressions for evaluation. Or try :help.

    scala> 
```

To run the Clojure shell:
```
    $ lein repl
    nREPL server started on port 52117 on host 127.0.0.1 - nrepl://127.0.0.1:52117
    REPL-y 0.3.7, nREPL 0.2.12
    Clojure 1.8.0
    Java HotSpot(TM) 64-Bit Server VM 1.8.0_172-b11
        Docs: (doc function-name-here)
              (find-doc "part-of-name-here")
      Source: (source function-name-here)
     Javadoc: (javadoc java-object-or-class-here)
        Exit: Control+D or (exit) or (quit)
     Results: Stored in vars *1, *2, *3, an exception in *e

    user=> 
```

Further Reading:

* <https://en.wikipedia.org/wiki/Interpreter_(computing)>,
  <https://en.wikipedia.org/wiki/Compiler>,
  <https://en.wikipedia.org/wiki/Interpreted_language>,
  <https://en.wikipedia.org/wiki/Compiled_language>
* for Clojure both, REPLs and a [compiler](https://clojure.org/reference/compilation), are available
* for Scala both, REPLs and a [compiler](https://www.scala-lang.org/files/archive/nightly/docs/manual/html/scalac.html), are available

------------

[<-- previous page](README.md)

[next page -->](/ch2_expressions.md)
