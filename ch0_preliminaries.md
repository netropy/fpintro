## 0. Preliminaries: Writing Text, the Markdown Language, the Scala and Clojure Language Shells (REPL)

To begin, some information on:

* how to write a "Markdown" text document (like this one),
* how to run Clojure and Scala code for the exercises.

#### 0.0.1 Inspect some file formats for text documents (like .html/.doc/.txt).

* MacOS: open TextEdit.app
```
    ->New ->...type something...
    ->Save .rtf/.html/.xml/.doc
    ->Format->Make Plain/Rich Text
    ->Save .txt
```
* What is a [text editor](https://en.wikipedia.org/wiki/Text_editor)?
* What is a [file format](https://en.wikipedia.org/wiki/File_format)? What is a [plain text](https://en.wikipedia.org/wiki/Plain_text) vs. a [binary file](https://en.wikipedia.org/wiki/Binary_file) format vs. [formatted text](https://en.wikipedia.org/wiki/Formatted_text)?

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

#### 0.0.2 Write formatted text in plain-text "Markdown" and render in a browser.

How to write Markdown texts: see [cheat-sheet](https://enterprise.github.com/downloads/en/markdown-cheatsheet.pdf) and [summary](https://guides.github.com/features/mastering-markdown)

___Further reading:___

* [Lightweight_markup_language](https://en.wikipedia.org/wiki/Lightweight_markup_language)
* Markdown: [cheat-sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), [basic writing and formatting syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax), [organizing information with tables](https://help.github.com/articles/organizing-information-with-tables), [creating and highlighting code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks)

How to view Markdown texts in a [web browser](https://en.wikipedia.org/wiki/Web_browser):

* Upload a markdown file to [Github](https://github.com/about) and view it in a web browser.
* What is a ["shell"](https://en.wikipedia.org/wiki/Shell_(computing))? What is a [command-line_interface](https://en.wikipedia.org/wiki/Command-line_interface) vs. a [graphical_user_interface](https://en.wikipedia.org/wiki/Graphical_user_interface)?
* To locally convert and render an .md file as .html, install [pandoc](https://pandoc.org) and run any of these commands in shell:
```
    $ pandoc -o topics.html topics.md
    $ pandoc topics.md -o topics.html
    $ pandoc topics.md > topics.html
```
* Open the generated .html file in a web browser.

___Notes:___

* Markdown is a simple format for styled editing and is easy to read and to write.
* Markdown is widely used and has become the format of choice for "collaborative" editing.
* Markdown can be easily converted to HTML, which is the standard markup language for web pages and web applications.
* Pandoc is just one of many tools converting .md to .html.
* Github automatically renders an .md file as .html for viewing and linking (embedded links to .md files carry over to the generated .html page).

#### 0.0.3 Install Java, Clojure, Scala and run the language shells (REPL)

Install manually or via a [package manager](https://en.wikipedia.org/wiki/Package_manager) (like [Homebrew](https://brew.sh) for [macOS](https://en.wikipedia.org/wiki/Macintosh_operating_systems)):

* [Java](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html), preferrably a "Java SE Development Kit": [OpenJDK](http://openjdk.java.net) or [Oracle's JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Leiningen](https://leiningen.org) for [Clojure](https://clojure.org)
* [Scala](https://www.scala-lang.org/download)

A _language shell_ or [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) reads (typically small) chunks of programming code as text input, then directly executes (evaluates) it, and prints the result as text output.  

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

To run the Scala shell:
```
    $ scala
    Welcome to Scala 2.12.5 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_172).
    Type in expressions for evaluation. Or try :help.

    scala> 
```

___Further Reading:___

* What is a [computer language](https://en.wikipedia.org/wiki/Computer_language) [interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)) vs a [compiler](https://en.wikipedia.org/wiki/Compiler)?  What is an [interpreted_language](https://en.wikipedia.org/wiki/Interpreted_language) vs a [compiled language](https://en.wikipedia.org/wiki/Compiled_language)?
* for Clojure both, [REPLs](https://clojure.org/guides/repl/launching_a_basic_repl) and a [compiler](https://clojure.org/reference/compilation), are available
* for Scala both, [REPLs](https://docs.scala-lang.org/overviews/repl/overview.html) and a [compiler](https://www.scala-lang.org/files/archive/nightly/docs/manual/html/scalac.html), are available

------------

[<-- previous page](README.md)

[next page -->](/ch2_expressions.md)
