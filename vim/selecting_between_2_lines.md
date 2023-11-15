Ever wondered how to select text between 2 given line numbers in vim

Prerequisite: You are aware of 2 linenumbers, between which text is to be visually selected in vim

Demo: Let say you have starting line number 30 and ending line number 63
This is the key combination that would work

```vim
30GV63G
```

30G goes to line number 30
V (shift + v) enables visual select for the entire line
63G goes to line number 63
