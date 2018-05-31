# bash-cheat-sheet
Bash string manipulation cheat sheet:

Find length of a string:
  string='abcdef'
  => echo ${#string}                    ## will print 6
  => echo `expr length $string`         ## will print 6
  => echo `expr "${string}" : '.*'`     ## will print 6

--- To-Be-Added ---
