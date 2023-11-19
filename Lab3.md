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
public void testReverseInPlace()
{
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

Here is the output of the code passing the test cases of the non-failure inducing inputs:
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/65ccee6b-4ed1-4e8d-a04b-b5817ec897b9)


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

Here is the output of the fixed code passing the test cases including the case of the failure inducing input
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/a5a298f7-4d3b-47c7-a7d6-3852089c13bb)


The problem was that the first elements in the array were simply being replaced by the last elements so by the time we wanted to replace the final elements with the original first elements, those first elements were overwritten by the final elements so they were just being repeated at the end. To fix this, we made a second empty array of the same size and copied the elements in reverse into the new array. Then, we looped through the original array and replaced every value with the appropriate value from the new array.



**PART 2**



I choose the `find` command.


1. `-name` This option searches for files by name
   
Example 1: `find ./technical -name "*.txt"`.  This command finds all `.txt` files in the `./technical` directory. This command is useful for quickly recursively locating and listing all the text files in a given directory. 

 Output: (This is just a sample of the output as the actual output is too big to fit on the screen UPDATE!!4)

```                                                                                                                                                        
umark@Umars-Laptop docsearch % find ./technical -name "*.txt"
./technical/plos/journal.pbio.0020187.txt
./technical/plos/pmed.0020116.txt
./technical/plos/pmed.0020102.txt
./technical/plos/journal.pbio.0020150.txt
./technical/plos/pmed.0020062.txt
./technical/plos/pmed.0020274.txt
./technical/plos/journal.pbio.0020232.txt
./technical/plos/journal.pbio.0030021.txt
./technical/plos/journal.pbio.0020224.txt
./technical/plos/pmed.0020048.txt
./technical/plos/pmed.0020060.txt
./technical/plos/pmed.0020074.txt
./technical/plos/journal.pbio.0020146.txt
./technical/plos/pmed.0020114.txt
./technical/plos/pmed.0010028.txt
./technical/plos/journal.pbio.0020350.txt
./technical/plos/journal.pbio.0020190.txt
./technical/plos/pmed.0010029.txt
./technical/plos/pmed.0020115.txt
./technical/plos/journal.pbio.0020147.txt
./technical/plos/pmed.0020075.txt
./technical/plos/pmed.0020061.txt
./technical/plos/pmed.0020210.txt
./technical/plos/pmed.0020238.txt
./technical/plos/journal.pbio.0030051.txt
./technical/plos/journal.pbio.0020068.txt
```
	

Example 2: `find ./technical -name "*research*"`: This command finds all files that contain `"research"` in the name. This command is useful for recursively locating and listing all files in a given directory that contain a certain word or phrase 

Output: (This is just a sample of the output as the actual output is too big to fit on the screen)

 
```bash
umark@Umars-Laptop docsearch % find ./technical -name "*research*"
./technical/biomed/gb-2001-2-4-research0010.txt
./technical/biomed/gb-2001-2-4-research0011.txt
./technical/biomed/gb-2002-3-9-research0043.txt
./technical/biomed/gb-2001-2-7-research0025.txt
./technical/biomed/gb-2002-3-7-research0032.txt
./technical/biomed/gb-2001-2-4-research0012.txt
./technical/biomed/gb-2001-2-7-research0024.txt
./technical/biomed/gb-2001-2-3-research0008.txt
./technical/biomed/gb-2002-3-9-research0046.txt
./technical/biomed/gb-2002-3-7-research0037.txt
./technical/biomed/gb-2001-2-8-research0027.txt
./technical/biomed/gb-2001-2-11-research0046.txt
./technical/biomed/gb-2001-2-8-research0032.txt
./technical/biomed/gb-2002-3-7-research0036.txt
./technical/biomed/gb-2002-3-9-research0051.txt
./technical/biomed/gb-2002-3-9-research0045.txt
./technical/biomed/gb-2001-2-8-research0030.txt
./technical/biomed/gb-2001-2-4-research0014.txt
./technical/biomed/gb-2001-2-11-research0045.txt
./technical/biomed/gb-2002-3-7-research0035.txt
./technical/biomed/gb-2001-2-8-research0031.txt
./technical/biomed/gb-2002-3-9-research0044.txt
./technical/biomed/gb-2002-3-2-research0008.txt
./technical/biomed/gb-2002-3-11-research0059.txt
./technical/biomed/gb-2002-3-11-research0065.txt
./technical/biomed/gb-2001-2-10-research0041.txt
./technical/biomed/gb-2002-3-8-research0040.txt
./technical/biomed/gb-2001-2-9-research0035.txt
./technical/biomed/gb-2002-3-12-research0085.txt
./technical/biomed/gb-2002-3-2-research0009.txt
./technical/biomed/gb-2002-3-12-research0087.txt
./technical/biomed/gb-2002-3-12-research0078.txt
./technical/biomed/gb-2001-2-6-research0018.txt
./technical/biomed/gb-2001-2-9-research0037.txt
```

Source: [man7.org](https://www.man7.org/linux/man-pages/man1/find.1.html)

(Found by Googling "find command name option")

3. `-type` This option allows you to choose the type of file to search for.
   
Example 1: `find ./technical -type f`. This command will find all regular files in the `./technical` directory. This command is useful if you need to recursively list all the files in a given directory and the directories inside of it.

 Output: (This is just a sample of the output as the actual output is too big to fit on the screen)


```bash
umark@Umars-Laptop docsearch % find ./technical -type f
./technical/plos/journal.pbio.0020187.txt
./technical/plos/pmed.0020116.txt
./technical/plos/pmed.0020102.txt
./technical/plos/journal.pbio.0020150.txt
./technical/plos/pmed.0020062.txt
./technical/plos/pmed.0020274.txt
./technical/plos/journal.pbio.0020232.txt
./technical/plos/journal.pbio.0030021.txt
./technical/plos/journal.pbio.0020224.txt
./technical/plos/pmed.0020048.txt
./technical/plos/pmed.0020060.txt
./technical/plos/pmed.0020074.txt
./technical/plos/journal.pbio.0020146.txt
./technical/plos/pmed.0020114.txt
./technical/plos/pmed.0010028.txt
./technical/plos/journal.pbio.0020350.txt
./technical/plos/journal.pbio.0020190.txt
./technical/plos/pmed.0010029.txt
./technical/plos/pmed.0020115.txt
```
 
Example 2: `find ./technical -type d`. This command will find all directories in the `./technical` directory. This command is useful if you need to recursively list all the directories inside and including a given directory while ignoring the files inside of it.

Output: (This is the entire output)


```bash
umark@Umars-Laptop docsearch % find ./technical -type d
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```


Source: [geeksforgeeks.org]https://www.geeksforgeeks.org/find-command-in-linux-with-examples

(Found by Googling "how to use find command linux")

5. `-mtime` This option finds files that were modified a certain amount of time ago.
   
Example 1: `find ./technical -mtime -7`: This command will find all files in the `./technical` directory that were modified less than 7 days ago. This command is useful for recursively finding and listing all files modified within the past week inside of a given directory. 

Output: (The output was empty since there were no files modified within the past 7 days)


```bash
umark@Umars-Laptop docsearch % find ./technical -mtime -7
```

Example 2: `find ./technical -mtime +7`: This command will find all files in the `./technical` directory that were modified more than 7 days ago. This command is useful for recursively finding and listing all files modified before the past week inside of a given directory. 

Output: (This is just a sample of the output as the actual output is too big to fit on the screen)


```bash
umark@Umars-Laptop docsearch % find ./technical -mtime +7
./technical/plos/pmed.0020102.txt
./technical/plos/journal.pbio.0020150.txt
./technical/plos/pmed.0020062.txt
./technical/plos/pmed.0020274.txt
./technical/plos/journal.pbio.0020232.txt
./technical/plos/journal.pbio.0030021.txt
./technical/plos/journal.pbio.0020224.txt
./technical/plos/pmed.0020048.txt
./technical/plos/pmed.0020060.txt
./technical/plos/pmed.0020074.txt
./technical/plos/journal.pbio.0020146.txt
./technical/plos/pmed.0020114.txt
./technical/plos/pmed.0010028.txt
./technical/plos/journal.pbio.0020350.txt
./technical/plos/journal.pbio.0020190.txt
./technical/plos/pmed.0010029.txt
```

First one contained no files since they were downloaded over a week ago, and the second contained all the files for the same reason.

Source: [Linuxize](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/)
	
 (Found by Googling "linux find command options")

7. `-size` This option searches for files based on their size.
   
Example 1: `find ./technical -size +1M`. This command will find all files in the `./technical` directory that are larger than 1 Megabyte. This command is useful for recursively finding and listing all the files inside of a given directory that are bigger than 1 Megabyte

Output: (The output is empty since there are no files inside the `./technical` directory that exceed 1 Megabyte in size)


 ```bash
  umark@Umars-Laptop docsearch % find ./technical -size +1M
  ```

Example 2: `find ./technical -size -1M`. This command will find all the files that are smaller than 1 Megabyte.This command is useful for recursively finding and listing all the files inside of a given directory that are smaller than 1 Megabyte

Output: (This is just a sample of the output as the actual output is too big to fit on the screen))


```bash
umark@Umars-Laptop docsearch % find ./technical -size -1M
./technical/plos/pmed.0020102.txt
./technical/plos/journal.pbio.0020150.txt
./technical/plos/pmed.0020062.txt
./technical/plos/pmed.0020274.txt
./technical/plos/journal.pbio.0020232.txt
./technical/plos/journal.pbio.0030021.txt
./technical/plos/journal.pbio.0020224.txt
./technical/plos/pmed.0020048.txt
./technical/plos/pmed.0020060.txt
./technical/plos/pmed.0020074.txt
./technical/plos/journal.pbio.0020146.txt
./technical/plos/pmed.0020114.txt
 ./technical/plos/pmed.0010028.txt
./technical/plos/journal.pbio.0020350.txt
./technical/plos/journal.pbio.0020190.txt
./technical/plos/pmed.0010029.txt
./technical/plos/pmed.0020115.txt
./technical/plos/journal.pbio.0020147.txt
./technical/plos/pmed.0020075.txt
./technical/plos/pmed.0020061.txt
./technical/plos/pmed.0020210.txt
./technical/plos/pmed.0020238.txt
./technical/plos/journal.pbio.0030051.txt
./technical/plos/journal.pbio.0020068.txt
 ```
  
 Second contains all the files and first contains none due to all the files in the `./technical` directory being smaller files.

Source: [Linuxize](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/)

(Found by Googling "linux find command options")
