Part 1: Bugs

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testAverageWithoutLowestFailure() {
    double[] input1 = { 3, 1, 5 };
    assertEquals(4.0, ArrayExamples.averageWithoutLowest(input1), 0.001);
	}

  @Test 
	public void testAverageWithoutLowestSuccess() {
    double[] input2 = { 3, 1, 5, 7 };
    assertEquals(5.0, ArrayExamples.averageWithoutLowest(input2), 0.001);
	}
}
```

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test 
  public void testAverageWithoutLowestFailure() {
    double[] input1 = { 3, 1, 5 };
    assertEquals(3.0, ArrayExamples.averageWithoutLowest(input1), 0.001);
  }

  @Test 
  public void testAverageWithoutLowestSuccess() {
    double[] input2 = { 3, 1, 5, 7 };
    assertEquals(4.666, ArrayExamples.averageWithoutLowest(input2), 0.001);
  }
}
```

The symptom of the issue will be apparent from the output of running the JUnit tests. 
The testAverageWithoutLowestFailure test should fail with the provided buggy implementation, 
whereas the testAverageWithoutLowestSuccess test will pass.

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
    return sum / (arr.length - 1); // This should be arr.length since we're considering all elements except the lowest
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
    return sum / arr.length; // Fixing the division by using arr.length instead of (arr.length - 1)
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

The -r (recursive) argument makes grep recursively search through directories and subdirectories for a specific pattern in files.

Chatgpt: write an example of grep -r using ./technical directory
Output code:
```
grep -r "search_term" ./technical
```

In the example above, grep searched for "search_term" recursively within the technical directory and all subdirectories, which is useful when you want to find a matching data stream in the specified directory and its subdirectories.

Chatgpt: write another example of grep -r using a different directory
Output code:
```
grep -r "search_term" .
```
This second example, grep recursively searches for the word "error" within the ```pwd``` directory and its subdirectories, useful for quickly finding mssages that say "error" in files.

Option: -i (ignore case)

Source: Found in the grep manual (man grep) and various online resources.

Description: This option makes grep case-insensitive, so it matches patterns regardless of case.

bash
Copy code
grep -i "pattern" file.txt
Output: This command searches for the pattern "pattern" in file.txt, ignoring the case of the letters.

bash
Copy code
grep -i "important" README.md
Output: This command searches for the word "important" in the README.md file, ignoring case, which can be helpful when you're not sure about the exact capitalization of the word you're searching for.

Option: -v (invert match)

Source: Learned about this option from the grep manual (man grep) and various online tutorials.

Description: This option inverts the sense of matching, displaying lines that do not contain the specified pattern.

bash
Copy code
grep -v "exclude_this" file.txt
Output: This command displays all lines in file.txt that do not contain the pattern "exclude_this".

bash
Copy code
grep -v "TODO" ./technical/*.txt
Output: This command searches for all .txt files in the ./technical directory and its subdirectories, displaying lines that do not contain the string "TODO", which can be useful for filtering out lines that don't need attention.

Option: -E (extended regular expressions)

Source: Found in the grep manual (man grep) and various online documentation.

Description: This option enables the use of extended regular expressions in grep, providing more advanced pattern matching capabilities.

bash
Copy code
grep -E "pattern1|pattern2" file.txt
Output: This command searches for lines in file.txt containing either "pattern1" or "pattern2" using extended regular expressions.

Copy code
grep -E "\b\d{3}-\d{3}-\d{4}\b" contacts.txt
Output: This command searches for lines in contacts.txt containing phone numbers in the format XXX-XXX-XXXX, using an extended regular expression to ensure precise matching.
