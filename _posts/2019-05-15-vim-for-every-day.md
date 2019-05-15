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
