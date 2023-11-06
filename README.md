# Lab-Report-3---Bugs-and-Commands-Week-5-
## Part 1 - Bugs

### A failure-inducing input for the buggy program, as a JUnit test and any associated code
@Test
  public void testReverseInPlaceFailure() {
  int[] input = {1, 2, 3, 4};
  ArrayExamples.reverseInPlace(input);
  assertArrayEquals(new int[]{4, 3, 2, 1}, input);
}

### An input that doesn’t induce a failure, as a JUnit test and any associated code
@Test
public void testReverseInPlaceNoFailure() {
  int[] input = {1};
  ArrayExamples.reverseInPlace(input);
  assertArrayEquals(new int[]{1}, input);
}
### The symptom, as the output of running the tests
Output of Running the Failed Test:
![Image](TestFailLab3.png)

Output of Running Passed Test:
![Image](TestPassLab3.png)

### The bug, as the before-and-after code change required to fix it
Old Buggy Code:
```java
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i++) {
    arr[i] = arr[arr.length - i - 1];
  }
}

New Fixed Code:
static void reverseInPlace(int[] arr) {
    int j = arr.length - 1;
    for(int i = 0; i < j; i++) {
      int temp = arr[i]; // Use 'temp' or another name that indicates a single value
      arr[i] = arr[j];
      arr[j] = temp;
      j--;
    }
  }
