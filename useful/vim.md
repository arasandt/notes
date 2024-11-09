:set paste --> to keep formatting e.x. when pasting xml
:set autoindent
:set shiftwidth=2
SHIFT V to get into visual mode
Select the rows
SHIFT > to move right or SHIFT , to move left
y<n>y then p, to duplicate the line.
'dG' - Deletes contents from cursor to end of file. This is very useful when editing YAML files.
'ZZ' - Save and exit quickly.
 
 
Normal Mode
j à Down
k à Up
l à Right
j à Left
move multiple lines use <number> + k
 
gg à BOF
G à EOF
 
w à word forward beginning letter (W including punctuations as part of word)
e à word forward ending letter (E including punctuations as part of word)
b à word back  word beginning letter (B including punctuations as part of word)
$ à goto end of line
0 à zero beginning of line
(use above with <numbers> to jump multiple words)
 
:13 à goto 13th line
/nginx à search for nginx (to get next/previous occurrence press n/N)
?nginx à backward search
f/F à forward/backward find a character (cant understand what it does)
 
Insert Mode (i)
i/I à insert before the cursor/BOL
a/A à append after the cursor/EOL
u à undo
s/S à remove the cursor/LINE and replace. Like under the cursor/LINE.
o/O à next/previous new line
 
Visual Mode (v)
v/V à selecting the character/LINE
 
Replace Mode (r)
r/R à replace the character/LINE
 
VIM Language
c à change
d à delete
y à copy or yank
p à paste
 
cw/cb à change the word front/back (puts you in insert mode too)
dw/db à delete the word front/back
yw/yb à copied the word front/back
cc/C à change the whole line
dd à delete the whole line
. à repeat previous action
D/d$ à delete everything from cursor to EOL
d0 à delete everything from cursor to BOL
c3w à change next 3 words and type to replace
ci{ à change inside bracket.
di{ à delete inside bracket.
ca{ à change the bracket block 
da{ à delete the bracket block
 
:%s/nginx/frontend/gc  à find replace global with confirmation
