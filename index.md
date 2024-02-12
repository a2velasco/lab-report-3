# Lab Report 3
## Part 1
The bug that I chose for part 1 is the bug in the for loop and return statement for the reversed method for ArrayExamples.

Current reversed method:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1]; // bug
    }
    return arr; // bug
  }
```
A failure inducing input:
```
@Test
  public void testReversed() {
    int[] input = {3, 2, 1, 0};
    assertArrayEquals(new int[]{0, 1, 2, 3}, ArrayExamples.reversed(input));
  }
```
Input that does not induce failure:
```
@Test
  public void testReversed() {
    int[] input = {0};
    assertArrayEquals(new int[]{0}, ArrayExamples.reversed(input));
  }
```
The symptom being that the array did not reverse correctly and instead had 0 at the index:
![Image](image.png)

The before and after fixing the bug:

Before reversed method:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1]; // bug
    }
    return arr; // bug
  }
```
After reversed method:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1]; // switched newArray and arr around so that it was not arr being assigned values.
    }
    return newArray; // return the correct array
  }
```
The fix addressed the issue because we were assigning the values of newArray, which was initialized to all 0, into arr which had our inputted values. I also made sure to return the correct array as we were just returning arr again instead of returning the new array that was created.

## Part 2
