---
published: true
---
### Basic search and replace

The :substitute command searches for a text pattern, and replaces it with a text string. There are many options, but these are what you probably want:

`:%s/foo/bar/g`
Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.

`:s/foo/bar/g`
Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.

`:%s/foo/bar/gc`
Change each 'foo' to 'bar', but ask for confirmation first.

`:%s/\<foo\>/bar/gc`
Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation.

`:%s/foo/bar/gci`
Change each 'foo' (case insensitive due to the i flag) to 'bar'; ask for confirmation.

`:%s/foo\c/bar/gc` is the same because \c makes the search case insensitive.
This may be wanted after using :set noignorecase to make searches case sensitive (the default).

`:%s/foo/bar/gcI`
Change each 'foo' (case sensitive due to the I flag) to 'bar'; ask for confirmation.

`:%s/foo\C/bar/gc` is the same because \C makes the search case sensitive.
This may be wanted after using :set ignorecase to make searches case insensitive.

#### Search range:

`:s/foo/bar/g`	Change each 'foo' to 'bar' in the current line.
`:%s/foo/bar/g`	Change each 'foo' to 'bar' in all the lines.
`:5,12s/foo/bar/g`	Change each 'foo' to 'bar' for all lines from line 5 to line 12 (inclusive).
`:'a,'bs/foo/bar/g`	Change each 'foo' to 'bar' for all lines from mark a to mark b inclusive (see Note below).
`:'<,'>s/foo/bar/g`	When compiled with +visual, change each 'foo' to 'bar' for all lines within a visual selection. Vim automatically appends the visual selection range ('<,'>) for any ex command when you select an area and enter :. Also, see Note below.
`:.,$s/foo/bar/g`	Change each 'foo' to 'bar' for all lines from the current line (.) to the last line ($) inclusive.
`:.,+2s/foo/bar/g`	Change each 'foo' to 'bar' for the current line (.) and the two next lines (+2).
`:g/^baz/s/foo/bar/g`	Change each 'foo' to 'bar' in each line starting with 'baz'.
Note: As of Vim 7.3, substitutions applied to a range defined by marks or a visual selection (which uses a special type of marks '< and '>) are not bounded by the column position of the marks by default. Instead, Vim applies the substitution to the entire line on which each mark appears unless the \%V atom is used in the pattern like: `:'<,'>s/\%Vfoo/bar/g`.

When searching:

., *, \, [, ^, and $ are metacharacters.
+, ?, |, &, {, (, and ) must be escaped to use their special function.
\/ is / (use backslash + forward slash to search for forward slash)
\t is tab, \s is whitespace (space or tab)
\n is newline, \r is CR (carriage return = Ctrl-M = ^M)
After an opening [, everything until the next closing ] specifies a /collection. Character ranges can be represented with a -; for example a letter a, b, c, or the number 1 can be matched with [1a-c]. Negate the collection with [^ instead of [; for example [^1a-c] matches any character except a, b, c, or 1.
\{#\} is used for repetition. /foo.\{2\} will match foo and the two following characters. The \ is not required on the closing } so /foo.\{2} will do the same thing.
\(foo\) makes a backreference to foo. Parenthesis without escapes are literally matched. Here the \ is required for the closing \).
When replacing:

`\r` is newline, `\n` is a null byte (0x00).
`\&` is ampersand (`&` is the text that matches the search pattern).
`\0` inserts the text matched by the entire pattern
`\1` inserts the text of the first backreference. `\2` inserts the second backreference, and so on.

### The substitute command can be used to insert (or replace) text. Here some examples:

`:s/^/new text/`
Insert "new text" at the beginning of the line.

`:s/$/new text/`	
Append "new text" to the end of the line.

`:s/green/bright &/g`
Replace each "green" with "bright green" in the line.

### To count the number of matches of a pattern, use the substitute command with the n flag. 

`:%s/pattern//gn` Shows the number of times that pattern matches text in the current buffer. 

`:%s/pattern//n` Omit g to display the number of lines where the pattern matches. 

`:10,50s/pattern//gn` To restrict the count to a region of the text, specify a range instead of % (% means all lines). For example, the above counts the number of occurrences in lines 10 to 50 inclusive. 

`:'<,'>s/pattern//gn` Counts the number of occurrences in the lines in the most recent visual selection.
