Part 1:

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
