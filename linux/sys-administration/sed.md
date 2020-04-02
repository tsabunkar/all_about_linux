# 'sed' command

- Replace a string in a file with a new string
- Find and delete a line
- This command is used - to manipulate text inside the file
- Remove empty lines from a files
- Remove the first or n line in a files
- To replace tabs with spaves
- Show defined lines from a file
- Substitute within vi-editor
- \$ cat avengers
- \$ cp avengers avengers-cp
- \$ sed 's/hulk/sulk/g' avengers [g -> replace globallly] (Replace hulk with sulk)
- \$ cat avengers (The above command only displayed, didn't modifiy/replace in the existing file)
- \$ sed -i 's/hulk/sulk/g' avengers (Now avengers file is modified where hulk is replaced by sulk globally throught)
- \$ cat avengers
- \$ sed '/man/d' avengers (find the string -> 'man' and remove/delete it, d-> delete)
- \$ sed '/^$/d' avengers (Remove empty lines form the files) [$ -> empty, ^ -> any]
- \$ sed '1d' avengers (delete the first line)
- \$ sed '3d' avengers (delete the first 3 lines)
- \$ sed 's/\t/ /g' avengers (replace tab to spaces)
- \$ sed 's/ /\t/g' avengers (replace spaces to tab)
- \$ sed -n 2,8p avengers (View from line 2nd to 8th)
- \$ sed 2,8p avengers (Not of above command)
- \$ sed G avengers (add empty line after previously existing string line)
- \$ vi avengers [lets c how to use sed in vim]
- \$ (normal mode) %s/man/mans/ [All the word 'man' is replaced with mans]
- \$ q! (quite without saving in vim)