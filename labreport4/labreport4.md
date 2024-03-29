SSH into the Server:
Keys Pressed: ```<s><s><h> <space> <a> <t> <z> <0> <0> <1>@ieng6-201.ucsd.edu <space> <enter>```
Explanation: Typed ```ssh atz001@ieng6-201.ucsd.edu``` and pressed ```<enter>``` to connect to the server.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s3.jpg)

Clone the Git Repository:
Keys Pressed:  ```<g><i><t><space><c><l><o><n><e><space><g><i><t><@><g><i><t><h><u><b><.><c><o><m>:<A><l><a><i><n><Z><h><a><n><g><S><t><u><d><e><n><t>/<l><a><b><7>.<g><i><t><enter>```
Explanation: Typed ```git clone git@github.com:AlainZhangStudent/lab7.git``` and pressed ```<enter>``` to clone the Git repository using ```ssh```.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s4.jpg)

Change Directory:
Keys Pressed: ```<c><d><space><l><a><b><7><enter>```
Explanation: Changed directory to ```lab7``` by typing ```cd lab7``` and pressing ```<enter>```.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s5.jpg)

Compile Java Files:
Keys Pressed: ```<j><a><v><a><c><space><-><c><p><space><.><colon>l<i><b>/<h><a><m><c><r><e><s><t><-><c><o><r><e><-><1><.><3><.><j><a><r>:<l><i><b>/<j><u><n><i><t><-><4><.><1><3><.><2><.><j><a><r><space>*.<j><a><v><a><enter>```
Explanation: Typed ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and pressed ```<enter>``` to compile the Java files.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s6.jpg)

Run JUnit Tests:
Keys Pressed: ```<j><a><v><a><space><-><c><p><space><.><colon>l<i><b>/<h><a><m><c><r><e><s><t><-><c><o><r><e><-><1><.><3><.><j><a><r>:<l><i><b>/<j><u><n><i><t><-><4><.><1><3><.><2><.><j><a><r><space>o><r><g><.<j><u><n><i><t>.<r><u><n><n><e><r>.<J><U><n><i><t>C><o><r><e><space><L><i><s><t><E><x><a><m><p><l><e><s><T><e><s><t><s><enter>```
Explanation: Typed ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` and pressed ```<enter>``` to run the JUnit tests.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s1.jpg)

Edit File:
Keys Pressed: ```<v><i><m><space>L<i><s><t><E><x><a><m><p><l><e><s><.><j><a><v><a><enter>```
Explanation: Opened the file ```ListExamples.java``` in ```vim``` by typing ```vim ListExamples.java``` and pressed ```<enter>```.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s7.jpg)

Navigate and Edit in Vim:
Keys Pressed: ```/<i>n<i>d<i>e<i>x><1> <down> <j> <h> <h> <h> <h> <h> <h> <i> <2> <esc> :<w><q> <enter>```
Explanation: Moved to the ```index1``` position using ```/index1```, navigated down one line with ```<down>```, pressed ```j``` to move down further, pressed ```h``` multiple times to move the cursor left, then pressed ```i``` to enter ```insert``` mode, typed ```2``` to insert the number ```2```, pressed ```<esc>``` to ```exit``` ```insert``` mode, and finally saved and exited ```vim``` by typing ```:wq``` and pressing ```<enter>```.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s8.jpg)

Compile Again:
Keys Pressed: ```<j><a><v><a><c><space><-><c><p><space><.><colon>l<i><b>/<h><a><m><c><r><e><s><t><-><c><o><r><e><-><1><.><3><.><j><a><r>:<l><i><b>/<j><u><n><i><t><-><4><.><1><3><.><2><.><j><a><r><space>*.<j><a><v><a><enter>```
Explanation: Typed ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and pressed ```<enter>``` to compile the ```Java``` files again.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s6.jpg)

Run JUnit Tests Again:
Keys Pressed: ```<j><a><v><a><space><-><c><p><space><.><colon>l<i><b>/<h><a><m><c><r><e><s><t><-><c><o><r><e><-><1><.><3><.><j><a><r>:<l><i><b>/<j><u><n><i><t><-><4><.><1><3><.><2><.><j><a><r><space>o><r><g><.<j><u><n><i><t>.<r><u><n><n><e><r>.<J><U><n><i><t>C><o><r><e><space><L><i><s><t><E><x><a><m><p><l><e><s><T><e><s><t><s><enter>```
Explanation: Typed ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` and pressed ```<enter>``` to run the JUnit tests again.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s2.jpg)

Stage Changes:
Keys Pressed:``` <g><i><t><space><a><d><d><space><.><enter>```
Explanation: Typed ```git add .``` and pressed ```<enter>``` to stage the changes.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s9.jpg)

Commit Changes:
Keys Pressed: ```<g><i><t><space><c><o><m><m><i><t><space><-><m><space><"><r><i><d><space><o><f><space><e><r><r><o><r><space>i><n><d><e><x><1><space><t><o><space>2><"><enter>```
Explanation: Typed ```git commit -m "rid of error in index1 to 2"``` and pressed ```<enter>``` to commit changes in local repository.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s10.jpg)

Git Push:
Keys Pressed:``` <g><i><t><space><p><u><s><h><enter>```
Explanation: Typed ```git push``` and pressed ```<enter>``` to push the changes to the remote repository.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport4/lab4s11.jpg)
