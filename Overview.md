# Java Prettify #



## Overview ##
This library is a java port of [Google Prettify](http://google-code-prettify.googlecode.com), the current version ported is 1-Jun-2011. The copyright holder of the
Google Prettify is Mike Samuel (mikesamuel@gmail.com). It is licensed under the [Apache license Version 2](http://www.opensource.org/licenses/Apache-2.0). This port is written by Chan Wai Shing (cws1989@gmail.com) distributed under
[Apache license Version 2](http://www.opensource.org/licenses/Apache-2.0).

  * If you need an editor more than a highlighter, please find [jsyntaxpane](http://code.google.com/p/jsyntaxpane/).
  * I port it for [Language Files Tool](http://code.google.com/p/language-files-tool/).

## Alternatives ##
[Java SyntaxHighlighter](http://code.google.com/p/java-syntax-highlighter/)

## Requirement ##
Java SE 6 or up

## Language Supported ##
The comments in [prettify.parser.Prettify](http://java-prettify.googlecode.com/svn/trunk/javadoc/prettify/parser/Prettify.html) are authoritative but the lexer should work on a number of languages including C and friends, Java, Python, Bash, SQL, HTML, XML, CSS, Javascript, and Makefiles. It works passably on Ruby, PHP, VB, and Awk and a decent subset of Perl and Ruby, but, because of commenting conventions, doesn't work on Smalltalk, or CAML-like languages.

LISPy languages are supported via an extension: [prettify.lang.LangLisp](http://java-prettify.googlecode.com/svn/trunk/javadoc/prettify/lang/LangLisp.html).

And similarly for Clojure, CSS, Go, Haskell, Lua, OCAML, SML, F#, Nemerle, Protocol Buffers, Scala, SQL, TeX, LaTeX, VHDL, Visual Basic, WikiText, XQuery, and YAML.

If you'd like to add an extension for your favorite language, please look at [prettify.lang.LangLisp](http://code.google.com/p/java-prettify/source/browse/trunk/src/prettify/lang/LangLisp.java) and file an [issue](http://code.google.com/p/google-code-prettify/issues/list) including your language extension, and a testcase.

Adapted from: http://google-code-prettify.googlecode.com/svn/trunk/README.html

## Themes ##
Default, Desert, Sons of Obsidian, Sunburst

[Click here to visit the gallery.](ThemesDemo.md)

## Configurations ##
  * Allows you to change the first (starting) line number.
  * Allows you to turn gutter with line numbers on and off.
  * Allows you to highlight one or more lines to focus user's attention.

[Click here for a demo.](ConfigurationsDemo.md)

## Example ##
<b><font color='red'>Note that this highlighter extends Swing component, so all operations are better be executed inside <a href='http://en.wikipedia.org/wiki/Event_dispatching_thread'>Swing dispatching thread</a>.</font></b>
```
import java.io.*;
import java.util.Arrays;
import java.util.logging.*;
import javax.swing.*;
import prettify.PrettifyParser;
import prettify.theme.ThemeDefault;
import syntaxhighlight.*;

public class Example {

  public static void main(String[] args) {
    SwingUtilities.invokeLater(new Runnable() {

      @Override
      public void run() {
        // the Prettify parser
        Parser parser = new PrettifyParser();

        // initialize the highlighter and use Default theme
        SyntaxHighlighter highlighter = new SyntaxHighlighter(parser, new ThemeDefault());
        // set the line number count from 10 instead of 1
        highlighter.setFirstLine(10);
        // set to highlight line 13, 27, 28, 38, 42, 43 and 53
        highlighter.setHighlightedLineList(Arrays.asList(13, 27, 28, 38, 42, 43, 53));
        try {
          highlighter.setContent(new File("test.html"));
        } catch (IOException ex) {
          Logger.getLogger(Example.class.getName()).log(Level.SEVERE, null, ex);
        }

        JFrame frame = new JFrame();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setContentPane(highlighter);
        frame.setLocationByPlatform(true);
        frame.pack();
        frame.setVisible(true);
      }
    });
  }
}
```

## Sample Screenshot ##
![http://java-prettify.googlecode.com/svn/wiki/ThemesDemo/ThemeDesert.png](http://java-prettify.googlecode.com/svn/wiki/ThemesDemo/ThemeDesert.png)

## Support & Discussion ##
[Support & Discussion Group](http://groups.google.com/group/java-prettify)

## Known Issues ##
  * Perl formatting is really crappy. Partly because Perl is [hard](http://www.perlmonks.org/?node_id=663393) to parse.

Adapted from: http://google-code-prettify.googlecode.com/svn/trunk/CHANGES.html