Part 1: Bugs
Failure inducing:
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3, 2, 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1, 2, 3 }, input1);
	}


  @Test
  public void testReversed() {
    int[] input1 = { 1 };
    assertArrayEquals(new int[]{ 1 }, ArrayExamples.reversed(input1));
  }
}
```
output:
 
Non-failure inducing:
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}


    @Test
    public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
}
```

The symptom of the issue will be apparent from the output of running the JUnit tests. 
The testReversed test and testReverseInPlace should fail with the provided buggy implementation, 
whereas the non-failure tests will pass given the buggy implementation.

Fixes:
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1); //should be arr.length since we're considering all elements except the lowest
}
```

```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / arr.length; //fix division using arr.length instead of (arr.length - 1)
}
```
The bug was caused by incorrect division in the averageWithoutLowest method, where the length of the array minus one was used instead of the actual length of the array. 
This caused incorrect average calculation in cases where the lowest number was excluded. 
The fix addresses the issue by using the correct length of the array for the division, ensuring that the average is calculated accurately.

Part 2: Researching Commands

I'm choosing the command grep. The 4 interesting options/alternate ways to use them I am exploring are:
-r (recursive), -i (case insensitive), -v (exclude pattern), and -E (extended regular expression). Something cool is that "grep -E is for extended regular expressions whereas -e is for basic regular expressions."

https://stackoverflow.com/questions/17130299/whats-the-difference-between-grep-e-and-grep-e

Source: 2.1.6 File and Directory Selection in https://www.gnu.org/software/grep/manual/grep.html

The ```-r``` (recursive) argument makes grep recursively search through directories and subdirectories for a specific pattern in files.

Chatgpt: write an example of grep -r using ```./technical``` directory
```
grep -r "search_term" ./technical
```
Output: searches for the pattern "search_term" in file.txt, recurseively in ```./technical``` directory.

In the example above, grep searched for "search_term" recursively within the technical directory and all subdirectories, which is useful when you want to find a matching data stream in the specified directory and its subdirectories.

Chatgpt: write another example of ```grep -r``` using the current directory
```
grep -r "search_term" .
```
Output: searches for the pattern "search_term" in files, recursively in ```pwd```.

This second example, grep recursively searches for the word "search_term" within the ```pwd``` directory and its subdirectories, useful for quickly finding messages that say "error" in files.

Source: Found in the grep manual (man grep) and various online resources.

The argument ```-i``` makes grep case-insensitive, so it matches patterns regardless of case (capital or lower case).

Chatgpt: write an example of ```grep -i``` using a file
```
grep -i "pattern" file.txt
```
Output: This command searches for the pattern "pattern" in file.txt, ignoring the case of the letters.

Chatgpt: write another example of ```grep -i``` using readme.md
```
grep -i "important" README.md
```
Output: This command searches for the word "important" in the README.md file, ignoring case, which can be helpful when you're not sure about the exact capitalization of the word you're searching for.

Source: Learned about this option from the grep manual (man grep) and various online tutorials.

The ```-v``` (invert match) argument inverts the sense of matching, displaying lines that do not contain the specified pattern.

Chatgpt: write an example of ```grep -i``` using a file
```
grep -v "exclude_this" file.txt
```
Output: This command displays all lines in file.txt that do not contain the pattern "exclude_this".

Chatgpt: write another example of ```grep -i``` using a file in the technical directory
```
grep -v "TODO" ./technical/*.txt
```
Output: This command searches for all .txt files in the ./technical directory and its subdirectories, displaying lines that do not contain the string "TODO", which can be useful for filtering out lines that don't need attention.


The ```-E``` (extended regular expressions) argument is found in the grep manual (man grep) and various online documentation, and it enables the use of extended regular expressions in grep, providing more advanced pattern-matching capabilities.

Chatgpt: write an example of ```grep -E``` using a file
```
grep -E "pattern1|pattern2" file.txt
```
Output: This command searches for lines in file.txt containing either "pattern1" or "pattern2" using extended regular expressions.

Chatgpt: write another example of ```grep -E``` using regex in a file called contacts
```
grep -E "\b\d{3}-\d{3}-\d{4}\b" contacts.txt
```
Output: This command searches for lines in contacts.txt containing phone numbers in the format XXX-XXX-XXXX, using an extended regular expression to ensure precise matching.
