# Vim

## Quick Commands

* `w`: until the start of the next word
* `e`: to the end of the current word
* `$`: to the end of the line
* `0`: to the beginning of the line
* `b`: to the beginning of the word
* `x`: delete the character under the cursor
* `X`: delete the character previous to the cursor
* `dw`: delete forward to the start of the next word
* `db`: delete back to the beginning of the word 
* `de`: delete forward the the end of the word
* `d$`: delete to the end of the line
* `i`: insert
* `a`: append at cursor
* `A`: append at the end of the line
* `I`: append at the beginning of the line
* `u`: undo the last command
* `f [char]`: move to the next given char in line
* `F [char]`: move to the previous char in line
* `;` and `,`: repeat last f or F
* `/yourtext and then: n, N`: search text
* `r[char]`: replace character below cursor
* `S`: clear current line; to insert mode
* `yy`: copy current line
* `P`: paste copied text after cursor
* `w`: forward one word
* `b`: backward one word
* `e`: move to the end of the word
* `ge`: move to the end of the previous word

## Movement

* `hjkl`
* `h` (left)  `j` (down)       `k` (up)      `l` (right)

```
       ^
       k        Hint:  The h key is at the left and moves left.
  < h     l >          The l key is at the right and moves right.
       j               The j key looks like a down arrow.
       v
```

asdfasdf f
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

## Navigation

* `w`, `b`: Move the cursor forward by a word or backward by a word.
* `0`, `$`: Move to the beginning or end of the current line.
* `gg`: Move to the beginning or end of the file.
*  `:<line-number>`: Move to a specific line number.

## Text selection

* `v`: Enter visual mode to select text character by character.
* `V`: Enter visual mode to select whole lines.

## Editing
i, I: Insert mode before the cursor or at the beginning of the line.
a, A: Insert mode after the cursor or at the end of the line.
o, O: Open a new line below or above the current line and enter insert mode.
x, X: Delete the character under the cursor or the character before the cursor.
dd: Delete the current line.
yy: Yank (copy) the current line.
p, P: Paste the yanked text after or before the cursor position.
`o`: insert new line below
`O`: insert new line above
`%`: go to corresponding parenthesis
`I`: insert at beginning of line


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