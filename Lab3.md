**PART 1**

I chose the bug in the `reverseInPlace` method where some of the original variable values were being overwritten too early.

A failure-inducing input for this method would be any set of more than 2 distinct elements.

Here is the code I used to find this:

``` java

@Test
 public void testReverseInPlaceAgain()
 {
   	int[] input1 = { 3, 5, 7 };
   	ArrayExamples.reverseInPlace(input1);
   	assertArrayEquals(new int[]{ 7,  5, 3 }, input1);
 }

```

The output of this test would be:
<img width="1044" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/d28d5393-a5a0-4ed1-b40c-66ac29b7927a">
(Ran through Test Explorer for convenience)

Here is an example of a valid test case:
``` java
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```

Here is the output for both these test cases run together:

<img width="698" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/338fca85-ccd8-45f8-83a2-bfb759894ea1">



Previous (buggy) code: 
``` java
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ```

Fixed code:
``` java
  static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for(int j = 0; j < arr.length; j += 1) {
      arr[j] = newArray[j];
    }
  }
```

The problem was that the first elements in the array were simply being replaced by the last elements so by the time we wanted to replace the final elements with the original first elements, those first elements were overwritten by the final elements so they were just being repeated at the end. To fix this, we made a second empty array of the same size and copied the elements in reverse into the new array. Then, we looped through the original array and replaced every value with the appropriate value from the new array.
