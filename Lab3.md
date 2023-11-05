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
