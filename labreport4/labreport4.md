SSH into the Server:
Keys Pressed: ```ssh atz001@ieng6-201.ucsd.edu <enter>```
Explanation: Typed ```ssh atz001@ieng6.ucsd.edu``` and pressed <enter> to connect to the server.

Clone the Git Repository:
Keys Pressed: ```git <space> clone <space> git<@>github<period>com<colon>AlainZhangStudent</>lab7<period>git <enter>```
Explanation: Typed ```git clone git@github.com:AlainZhangStudent/lab7.git``` and pressed <enter> to clone the Git repository using ```ssh```.

Change Directory:
Keys Pressed: ```cd <space> lab7 <enter>```
Explanation: Changed directory to ```lab7``` by typing ```cd lab7``` and pressing <enter>.

Compile Java Files:
Keys Pressed: ```javac<space><dash>cp<space><period><colon>lib<slash>hamcrest<dash>core<dash>1<period>1<.><j><a><r>:<l><i><b>/<j><u><n><i><t><-><4><.><1><3><.><2><.><j><a><r><space>*.<j><a><v><a><enter>```
Explanation: Typed 'javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java' and pressed <enter> to compile the Java files.

Run JUnit Tests:
Keys Pressed: ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>```
Explanation: Typed 'java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests' and pressed <enter> to run the JUnit tests.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s1.jpg)

Edit File:
Keys Pressed: ```vim listexamples.java <enter>```
Explanation: Opened the file 'ListExamples.java' in Vim by typing 'vim listexamples.java' and pressed <enter>.

Navigate and Edit in Vim:
Keys Pressed: ```/index1 <down> j h h h h h i 2 <esc> :wq <enter>```
Explanation: Moved to the 'index1' position using /index1, navigated down one line with <down>, pressed j to move down further, pressed h multiple times to move the cursor left, then pressed i to enter insert mode, typed 2 to insert the number 2, pressed <esc> to exit insert mode, and finally saved and exited Vim by typing :wq and pressing <enter>.

Compile Again:
Keys Pressed: ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>```
Explanation: Typed 'javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java' and pressed <enter> to compile the Java files again.

Run JUnit Tests Again:
Keys Pressed: ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>```
Explanation: Typed 'java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests' and pressed <enter> to run the JUnit tests again.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s2.jpg)

Stage Changes:
Keys Pressed: ```git add . <enter>```
Explanation: Typed 'git add .' and pressed <enter> to stage the changes.

Commit Changes:
Keys Pressed: ```git commit -m "rid error in index1 to 2" <enter>```
Explanation: Typed 'git commit

Git Push:
Keys Pressed: ```git push <enter>```
Explanation: Typed 'git push' and pressed <enter> to push the changes to the remote repository.
