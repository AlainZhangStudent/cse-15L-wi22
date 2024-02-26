Part 1: Bugs
Failure inducing:
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = { 1 };
    assertArrayEquals(new int[]{ 1 }, ArrayExamples.reversed(input1));
  }
}
```
output:

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport3/lab3s1.jpg)

Non-failure inducing:
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
    @Test
    public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
}
```
output:


![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport3/lab3s2.jpg)

The symptom of the issue will be apparent from the output of running the JUnit tests. 
The testReversed test should fail with the provided buggy implementation, 
whereas the non-failure tests will pass given the buggy implementation.

Fixes:

Before when buggy
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
After when fixed
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
}
```
The bug in the second reversed method arises from the incorrect assignment of values. Within the for loop, each element of the original array ```arr``` is assigned to the corresponding ```index``` in the ```newArray```, but with reversed indices. However, instead of assigning the reversed value of ```arr[i]``` to ```newArray[i]```, the code assigns the reversed value of ```newArray[i]``` to ```arr[i]```. This results in arr containing the reversed values of newArray, which were initially all zeros, effectively overwriting the original values of arr.

The fix involves correctly assigning the reversed values of ```arr``` to ```newArray```, ensuring that the original values of ```arr``` are preserved. Adjusting the assignment within the for loop to ```newArray[i] = arr[arr.length - i - 1]```;, the reversed values of ```arr``` are correctly stored in ```newArray```, resolving the bug and preserving the integrity of the original array.

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport3/lab3s3.jpg)

Part 2: Researching Commands

I'm choosing the command ```grep```. The 4 interesting options/alternate ways to use them I am exploring are:
```-r``` (recursive), ```-i``` (case insensitive), ```-v``` (exclude pattern), and ```-E``` (extended regular expression). Something cool is that "```grep -E``` is for extended regular expressions whereas ```-e``` is for basic regular expressions."

https://stackoverflow.com/questions/17130299/whats-the-difference-between-grep-e-and-grep-e

Source: 2.1.6 File and Directory Selection in https://www.gnu.org/software/grep/manual/grep.html

The ```-r``` (recursive) argument makes ```grep``` recursively search through directories and subdirectories for a specific pattern in files.

Chatgpt: write an example of ```grep -r``` using ```./technical``` directory
```
grep -r "search_term" ./technical
```
Output: searches for the pattern ```search_term``` in ```file.txt```, recurseively in ```./technical``` directory.

In the example above, ```grep``` searched for ```"search_term"``` recursively within the ```technical``` directory and all subdirectories, which is useful when you want to find a matching data stream in the specified directory and its subdirectories.

Chatgpt: write another example of ```grep -r``` using the current directory
```
grep -r "search_term" .
```
Output: searches for the pattern ```"search_term"``` in files, recursively in ```pwd```.

This second example, grep recursively searches for the word ```"search_term"``` within the ```pwd``` directory and its subdirectories, useful for quickly finding messages that say ```"error"``` in files.

Source: Found in the ```grep``` manual (```man grep```) and various online resources.

The argument ```-i``` makes ```grep``` case-insensitive, so it matches patterns regardless of case (capital or lower case).

Chatgpt: write an example of ```grep -i``` using a file
```
grep -i "pattern" file.txt
```
Output: This command searches for the pattern ```"pattern"``` in ```file.txt```, ignoring the case of the letters.

Chatgpt: write another example of ```grep -i``` using ```readme.md```
```
grep -i "important" README.md
```
Output: This command searches for the word "```important```" in the ```README.md``` file, ignoring case, which can be helpful when you're not sure about the exact capitalization of the word you're searching for.

Source: Learned about this option from the ```grep manual``` (```man grep```) and various online tutorials.

The ```-v``` (invert match) argument inverts the sense of matching, displaying lines that do not contain the specified pattern.

Chatgpt: write an example of ```grep -i``` using a file
```
grep -v "exclude_this" file.txt
```
Output: This command displays all lines in ```file.txt``` that do not contain the pattern "```exclude_this```".

Chatgpt: write another example of ```grep -i``` using a file in the technical directory
```
grep -v "TODO" ./technical/*.txt
```
Output: This command searches for all ```.txt``` files in the ```./technical``` directory and its subdirectories, displaying lines that do not contain the string "```TODO```", which can be useful for filtering out lines that don't need attention.


The ```-E``` (extended regular expressions) argument is found in the ```grep``` manual (```man grep```) and various online documentation, and it enables the use of extended regular expressions in grep, providing more advanced pattern-matching capabilities.

Chatgpt: write an example of ```grep -E``` using a file
```
grep -E "pattern1|pattern2" file.txt
```
Output: This command searches for lines in ```file.txt``` containing either "```pattern1```" or "```pattern2```" using extended regular expressions.

Chatgpt: write another example of ```grep -E``` using regex in a file called contacts
```
grep -E "\b\d{3}-\d{3}-\d{4}\b" contacts.txt
```
Output: This command searches for lines in ```contacts.txt``` containing phone numbers in the format XXX-XXX-XXXX, using an extended regular expression to ensure precise matching.
