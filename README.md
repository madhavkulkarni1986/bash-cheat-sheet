
bash-cheat-sheet

Ceat sheet for bash string operations:

#--------------------------------------

All the below commands are tested on

#--------------------------------------

DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=14.04

DISTRIB_CODENAME=trusty

DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"

++++++++++++++++++++++++++++++++++++++++++++++++

Find length of a string:

string='abcdef'

  => echo ${#string}                            ## will print 6
  
  => echo expr length $string           ## will print 6
  
  => echo expr "${string}" : '.*'       ## will print 6
  

Working with Sub Strings:

string='abcdefghij'

  => echo ${string:3}                           ## prints defghij; Print the substring of $string starting at 3rd index; based on zero indexing

  => echo ${string:3:2}                         ## prints de; Print the substring of $string starting at 3rd index and of length 2

  => echo ${string: -4}                         ## prints ghij; Print the last 4 characters of the string; Mind the space between colon(:) and hyphen(-). You can use small brackets around -4, like (-4)

  => echo ${string:(-4):2}                      ## prints gh; Print 2 characters starting at 4th character from the end

String manipulation:

string='abcxyzabc'

  => echo ${string#a*c}                         ## prints xyzabc; Strip the shortest match of ac(inclusive) from the given string

  => echo ${string##a*c}                        ## no output; will strip everything between ac(inclusive) in the longest match

    -> echo ${string##ab}                       ## prints c(to make the above clearer) this will strip everything from 'a' to the last 'b' and leaves only 'c'

  => echo ${string%ac}                          ## prints abcxyz; removes the occurance of ac(i.e abc) starting from the end

  => echo ${string%%ac}                         ## no output; removes everyting in between a and c for the longest match

  => echo ${string//xyz}                        ## prints abcabc; strip all occurance of xyz

  => echo ${string/abc/xyz}                     ## prints xyzxyzabc; replace first occurance of abc with xyz

  => echo ${string//abc/xyz}            ## prints xyzxyzxyz; replace all occurance of abc with xyz

  => echo ${string/#abc/mno}            ## prints mnoxyzabc; replace abc with mno if abc occurs at the beginning of the string

  => echo ${string/%abc/mno}            ## prints abcxyzmno; replace abc with mno if abc occurs at the en of the string

Operation to toggle between upper case and lower case of a string:

string="aBcDeFgHiJ"

  => echo ${string^^}                           ## prints ABCDEFGHIJ; convert all the lower case characters of the string to uppercase

  => echo ${string^}                            ## prints ABcDeFgHiJ; convert only the case of first character to upper

  => echo ${string^^[abcde]}            ## prints ABCDEFgHiJ; converts only the set of character [abcde] to upper case

  => echo ${string,}                            ## prints aBcDeFgHiJ; converts only the first character of the string from upper to lower

  => echo ${string,,}                           ## prints abcdefghij; converts all the character of the string from upper to lower

  => echo ${string,,[abcde]}            ## prints abcdeFgHiJ; converts only the set of character [abcde] to lower case

  => echo ${string~~}                           ## prints AbCdEfGhIj; Toggle between upper and lower case, meaning convert upper ccase chars to lower and vice-versa

  => echo ${string~}                            ## prints ABcDeFgHuJ; Toggle only the first characters case, from lower to upper or vice-versa

  => echo ${string~~[aBcDe]                     ## prints AbCdEFgHiJ; Toggles only the characters in set [aBcDe] from upper to lower or vice-versa

Value assignments for a string variable

str1=abc

str2=""

  => echo ${str1:-jerry}                        ## prints abc; if str1 is not defined or null, print jerry

  => echo ${str2:-jerry}                        ## prints jerry; str2 is not defined. So, jerry is printed

  => echo ${str1:=jerry}                        ## prints abc; if str1 is not defined assign jerry to it and print. In this case, str1 is defined, so mabc is printed

  => echo ${str2:=jerry}                        ## prints jerry; str2 is not defined. So, jerry is assigned to str2 and its printed. if you echo $str2, you will get jerry

## If you are copy pasting the commands, reset the value str2 to empty at this point, i.e str2="" Because it contains 'jerry' from above command

  => echo ${str1:+jerry}                        ## prints jerry; if str1 is set, print jerry, if its not set do not set or print anything. like below

  => echo ${str2:+jerry}                        ## prints nothing; since str2 is empty, it does not prints or assigns anything

