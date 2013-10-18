---
layout: manpage
title: grep(1)
permalink: /manpage/
categories:
tags: [man1]
---

## NAME

`grep`, `egrep`, `fgrep`, `zgrep`, `zegrep`, `zfgrep` -- file pattern searcher

## SYNOPSIS

`grep` [`-abcdDEFGHhIiJLlmnOopqRSsUVvwxZ`] [`-A` num] [`-B` num] [`-C`[num]] [`-e` pattern] [`-f` file] [`--binary-files`=value] [`--color`[=when]] [`--colour`[=when]] [`--context`[=num]] [`--label`] [`--line-buffered`] [`--null`] [pattern] [_file_ ...]

## DESCRIPTION

The `grep` utility searches any given input files, selecting lines that match one or more patterns.By default, a pattern matchesvan input line if the regular expression (RE) in the pattern matches the input line without its trailing newline.  An empty expression matches every line.  Each input line that matches at least one of the patterns is written to the standard output.

`grep` is used for simple patterns and basic regular expressions (BREs); egrep can handle extended regular expressions (EREs).  See re_format(7) for more information on regular expressions.  fgrep is quicker than both grep and egrep, but can only handle fixed patterns (i.e. it does not interpret regular expressions).  Patterns may consist of one or more lines, allowing any of the pattern lines to match a portion of the input.

`zgrep`, `zegrep`, and `zfgrep` act like `grep`, `egrep`, and `fgrep`, respectively, but accept input files compressed with the compress(1) or gzip(1) compression utilities.

The following options are available:

  * `-A` _num_, `--after-context`=_num_  
             Print num lines of trailing context after each match.  See also the -B and -C options.

  *  `-a`, `--text`
             Treat all files as ASCII text.  Normally grep will simply print ``Binary file ... matches'' if files contain binary char-
             acters.  Use of this option forces grep to output lines matching the specified pattern.

  *  `-B` _num_, `--before-context`=_num_
             Print num lines of leading context before each match.  See also the -A and -C options.

  *  `-b`, `--byte-offset`
             The offset in bytes of a matched pattern is displayed in front of the respective matched line.

## EXIT STATUS

The `grep` utility exits with one of the following values:

```
0        One or more lines were selected.  
1        No lines were selected.  
>1       An error occurred.
```

## EXAMPLES
To find all occurrences of the word `patricia' in a file:

    $ grep 'patricia' myfile

To find all occurrences of the pattern `.Pp' at the beginning of a line:

    $ grep '^\.Pp' myfile

The apostrophes ensure the entire expression is evaluated by `grep` instead of by the user's shell.  The caret \`^' matches the null
string at the beginning of a line, and the \`\' escapes the `.', which would otherwise match any character.

To find all lines in a file which do not contain the words \`foo' or \`bar':

    $ grep -v -e 'foo' -e 'bar' myfile

A simple example of an extended regular expression:

    $ egrep '19|20|25' calendar

Peruses the file `calendar' looking for either 19, 20, or 25.

## SEE ALSO
ed(1), ex(1), gzip(1), sed(1), re_format(7)

## STANDARDS
The `grep` utility is compliant with the IEEE Std 1003.1-2008 (``POSIX.1'') specification.

The flags [`-AaBbCDdGHhIJLmoPRSUVwZ`] are extensions to that specification, and the behaviour of the `-f` flag when used with an empty pattern file is left undefined.

All long options are provided for compatibility with GNU versions of this utility.

Historic versions of the `grep` utility also supported the flags [`-ruy`].  This implementation supports those options; however, their use is strongly discouraged.

## HISTORY
The `grep` command first appeared in Version 6 AT&T UNIX.