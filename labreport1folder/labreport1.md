Working directory for all was in ```/home```


![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport1folder/ls.png)


Ls with no arguments outputted the available directories and files in pwd because ls lists all the present files and folders 

Ls with a path to a directory outputted available directories and files in the given path because ls lists all the present files and folders, and in this case, everything present in the path of the directory

Ls with a path to a file outputted the path to the file itself which makes sense because if you list a singular file that's itself then it'll return itself


![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport1folder/cd.png)


Cd with no arguments outputted nothing because no directory was specified

Cd with an argument to a directory changed the prompt torreflect that pwd is inputted directory because you cd (changed directory) to that specified directory

Cd with an argument to a file gave an error ```bash: cd: messages/en-us.txt: Not a directory``` since it is not a directory


![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport1folder/cat.png)


Cat with no arguments stdout whatever arguments came after the command, which makes sense since cat reads the contents/reads its arguments and echoes it back

Cat with an argument to a path to a directory echoes back the type of object it is, i.e a directory, and its name because a directory isn't a text file that can be read sequentially. So its an error.

Cat with an argument to a text file (or path to a txtfile) will echo out its contents which makes sense because cat command reads its arguments and its contents
