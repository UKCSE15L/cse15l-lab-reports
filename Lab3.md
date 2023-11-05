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



**PART 2**



I choose the `find` command.

1. `-name` This option searches for files by name
   
	Example 1: `find ./technical -name "*.txt"`.  This command finds all `.txt` files in the `./technical` directory.

 	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/650a39c9-e4c7-4190-aa93-ab8533c5dee4)


	Example 2: `find ./technical -name "*research*"`: This command finds all files that contain `"research"` in the name

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/10136da1-9603-422e-9eb1-dce84fa32603)


	Source: [man7.org](https://www.man7.org/linux/man-pages/man1/find.1.html) (Found by Googling "find command name option")

3. `-type` This option allows you to choose the type of file to search for.
   
	Example 1: `find ./technical -type f`. This command will find all regular files in the `./technical` directory.

 	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/b97ca7f2-5aca-4ba0-8e2b-87ffb232e489)


	Example 2: `find ./technical -type d`. This command will find all directories in the `./technical` directory.

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/adc65efb-3588-4f0e-ba19-955aacebcb9a)


	Source: [geeksforgeeks.org]https://www.geeksforgeeks.org/find-command-in-linux-with-examples (Found by Googling "how to use find command linux")

5. `-mtime` This option finds files that were modified a certain amount of time ago.
   
	Example 1: `find ./technical -mtime -7`: This command will find all files in the `./technical` directory that were modified less than 7 days ago.

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/75d652fd-44b6-4772-9481-f0b2d3fa4357)

	Example 2: `find ./technical -mtime +30`: This command will find all files in the `./technical` directory that were modified more than 30 days ago.

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/c3a9ae96-4661-4268-94d5-f515b3d4a25f)


 	First one contained all the files since they were downloaded recently and second contained no files for the same reason.

	Source: [Linuxize](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/) (Found by Googling "linux find command options")

7. `-size` This option searches for files based on their size.
   
	Example 1: `find ./technical -size +1M`. This command will find all files in the `./technical` directory that are larger than 1 Megabyte.

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/a6f4593c-e40c-4220-a97c-0b15ccf30692)

	Example 2: `find ./technical -size -1M`. This command will find the that are smaller than 1 Megabyte.

	Output: ![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/4f4b1d25-b701-49ac-9f71-9034218e1f26)


 	Second contains all the files and first contains none due to them being smaller files.

	Source: [Linuxize](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/) (Found by Googling "linux find command options")
