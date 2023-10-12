# Vim

## Quick Commands

* `w`: forward one word 
* `e`: move to the end of the current word 
* `b`: back one word
* `ge`: to the end of the previous word (`g` means go, `e` means end)
* `$`: to the end of the line
* `0`: to the beginning of the line
* `^`: move to the first non-blank character of the line
* `}`: move forward a paragraph
* `{`: move back a paragraph
* `x`: delete the character under the cursor
* `X`: delete the character previous to the cursor
* `S`: clear current line; to insert mode
* `s`: clear current character; to insert mode
* `dw`: delete forward to the start of the next word
* `db`: delete back to the beginning of the word 
* `de`: delete forward the the end of the word
* `d$`: delete to the end of the line
* `d0`: delete to the beginning of the line
* `dd`: copy and delete current line
* `dG`: delete to end of file
* `dgg`: delete to beginning of file
* `daw`: delete current word and go to command mode ("delete a word")
* `caw`: change a word and go to end of previous word in insert mode
* `ciw`: change innner word (delete current word and go to insert mode)
* `d{`: delete to end of paragraph
* `d{`: delete to beginning of paragraph
* `di{`: delete the text inside the nearest pair of curly braces
* `ci{`: change the text inside the nearest pair of curly braces
* `vi{`: select the text inside the nearest pair of curly braces
* `ci(`: change the text inside the nearest parenthesis
* `di(`: delete the text inside the nearest parenthesis
* `vi(`: select the text inside the nearest parenthesis
* `cc`: change current line
* `ciw`: change inner word (delete current word and go to insert mode)
* `i`: insert at cursor
* `a`: append at cursor
* `I`: append at the beginning of the line
* `A`: append at the end of the line
* `ea`: append at end of word (`e` moves to end of word, `a` appends)
* `bi`: insert at beginnig of word (`b` moves to beginning, `i` inserts)
* `u`: undo the last command
* `f [char]`: move to the next given char in line
* `F [char]`: move to the previous char in line
* `;` and `,`: repeat last f or F
* `/` start a forward search
* `?`: start a backward search
* `n`: move to the next search result
* `N`: move to the previous search result
* `r`: replace character below cursor
* `R`: enter replace mode to overwrite text
* `J`: joing the current line with the line below it
* `yy`: copy current line
* `yyp`: duplicate current line below (copy and paste) 
* `yyP`: duplicate current line above (copy and paste) 
* `P`: paste copied text after cursor
* `gg`: move to the beginning of the file
* `G`: move to the end of the file
* `v`: start visual mode to select text character by character
* `V`: Start visual line mode to select lines.
* `Vk`: visual select up
* `Vj`: visual select down
* `V}`: visual select forward a paragraph
* `V{`: visual select backward a paragraph
* `>>`: indent the current line to the right
* `<<`: indent the current line to the left
* `zo` - open a fold under the cursor
* `zc` - close a fold under the cursor
* `zM` - close all folds in the current buffer
* `zR` - open all folds in the current buffer
* `h` (left) `j` (down, looks like an arrow) `k` (up) `l` (right)

## Commands

`operator   [number]   motion`

Operators are actions, like `d`. Number is an optional count to repeat the motion. Motions are what the action will operate on. Example motions:

* `w` - until the start of the next word
* `e` - to the end of the current word
* `$` - to the end of the line

### Deletion

* `dw`: delete a word
* `d$`: delete to the end of the line
* `d2w`: using a count to delete more than one word
* `dd`: delete a whole line
* `2dd`: delete two lines

### Using a count for deleteion

* `d2w`: using a count to delete more than one word
* `2dd`: delete two lines

### Using a count for a motion

Typing a number before a motion repeats it that many times.

* `2w`: move the cursor two words forward
* `e3`: move the cursor to the end of the third word forward
* `0`: move to the start of the line

## Search and replace
/: Search forward.
?: Search backward.
:s/pattern/replacement/g: Replace all occurrences of "pattern" with "replacement" in the current line.
:%s/pattern/replacement/g: Replace all occurrences of "pattern" with "replacement" in the entire file.

## Marks

ma, 'a: Set a mark named 'a' at the current cursor position.
'a: Jump to the position of mark 'a'.

# Miscellaneous

`.`: Repeat the last change.