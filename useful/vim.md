# This file provides information of VIM Commands

### Keep formatting when pasting xml 
:set paste / :set autoindent / :set shiftwidth=2

### Get into Visual Mode
SHIFT V

### Move right
Select the rows, SHIFT >

### Move left
Select the rows, SHIFT ,

### Duplicate the line
y(number)y then p where number is the number of lines and p means paste

### Delete ontents from cursor to end of file
dG This is very useful when editing YAML files.

### Save and exit quickly
ZZ
 
### Normal Mode
j is Down
k is Up
l is Right
j is Left

### Move multiple lines
(number) and k 
 
### Beginning of file
gg

### End of file
GG
 
### Word forward beginning letter without punctuations as part of word / with punctuations as part of word
w / W

### Word forward ending letter without punctuations as part of word / with punctuations as part of word
e / E

### Word backword ending letter without punctuations as part of word / with punctuations as part of word
b / B

### Goto end of line
$

### Beginning end of line
0

### Use above with (numbers) to jump multiple words

### Goto a specific line
:(number)
Example: :13 to goto 13th line

### To search for a text forward
/(word)
Example: /nginx to search for nginx 
While in search to get to next/previous occurrence press n/N

### To search for a text backward
?(word)

### Insert mode (i)
i for inserting before the cursor
I for inserting before end of line
a for appending before the cursor
A for appending before end of line
o for inserting new line after
O for iserting new line before

### Undo
u

### Visual Mode (v)
v for selecting the character
V for selecting the LINE
 
### Replace Mode (r)
r for selecting the character
R for selecting the LINE

### VIM Language
c for change
d for delete
y for copy or yank
p for paste

### Change the word (also puts you into insert mode)
cw for changing the word front
cb for changing the word back 
dw for deleting the word front
db for deleting the word back 
yw for copying the word front
yb for copying the word back 
cc or C for chanding the whole line
dd to delete the whole line
. to repeat previous action
D or d$ to delete everything from cursor to EOL (end of line)
d$ to delete everything from cursor to BOL (beginning of line)

c(number)w to change next number words and type to replace. Example: c3n to change next 3 words

### Find replace globally with confirmation
%s/(text1)/(text2)/gc
Example :%s/nginx/frontend/gc
