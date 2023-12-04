**Part 1**

Student: "Hello, I am a normal student writing an EdStem post as I need help debugging my program. I am having some trouble with my autograder, particularly one of the repositories from week 6 is causing me great trouble and anguish! My `grade.sh` bash script runs perfectly for all of the repositories except for the `list-methods-filename` repository. I know that this repository, which is my failure-inducing input, has the wrong name for the java file, but do not know what else to do or where to start debugging! I am totally freaking out, please help! I am including the terminal output which contains the symptom of the bug down below. Please help me TA, you are my only hope!" 

<img width="808" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/6f3c6397-75ef-4b5c-944d-7a296df1d57e">



TA (Teaching Assistant): "Yo what is up normal student, I am a totally normal TA or Teaching Assistant, have no fear as it is my duty to help you along the debugging process. Looking at the symptom you provided, it appears that there is not a problem in the `grade.sh` script at all. It looks like the error may actually be in the `TestListExamples` class! If you look closely at the stack trace, you can clearly see that all of the errors are in lines that reference the `ListExamples` java file. If you look even closer, you may notice that the same error is being repeated, the symbol cannot be found. Maybe start your debugging in the `TestListExamples` class, you mentioned that the provided repository uses a different name for the java file, perhaps the error has something to do with that."


Student: "Wow, thank you for the response! After looking into the `TestListExamples` class, I realized that all of the test methods were hard-coded to work on the `ListExamples` java file, but there were no measures to account for if that file didn't exist or went by a different name. Including a screenshot below of some of the test methods so you can get a general idea."

<img width="531" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/ff80153d-0e8e-4fb1-9d59-c2aa6ecd5df7">

That concludes the EdStem portion of my lab report.

The File and Directory structure needed to run my `grade.sh` bash script is as follows: You need the `grade.sh` shell script as well as the `TestListExamples.java` file and the `lib` directory. The `grade.sh` script initializes all the other files you need.

Here is the content of the `grade.sh` script:


``` shell script
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission 
echo 'Finished cloning'


file=`(find ./student-submission -name "*.java")`

if ! [[( -e $file )]]
then   
echo "File does not exist"
exit
fi

echo $file
cp -r $file grading-area
cp TestListExamples.java grading-area
cp -r lib grading-area
cd grading-area

echo 'Finished copying'

javac -cp $CPATH *.java

if [[( $? -ne 0 )]]
then   
echo "Compile Error - please see error message and fix."
exit
fi

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > tests.txt

echo "Tests ran"

allPassed=`(grep "OK" tests.txt | wc -l)`

grep ") t" tests.txt > failedtests.txt

failurecount=$(wc -l < failedtests.txt)
failurecount=$((9-failurecount))

if [[ $allPassed -ne 0 ]]
then
echo "9/9 Tests Passed! Congratulations!"
else
echo "Failed Tests:"
cat failedtests.txt
echo "You passed $failurecount/9 tests"
fi
```


Here is the content of the `TestListExample.java` file:

``` java
import static org.junit.Assert.*;
import org.junit.*;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeLeftEnd() {
    List<String> left = Arrays.asList("a", "d");
    List<String> right = Arrays.asList("a", "b", "c");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeEmptyLeft() {
    List<String> left = new ArrayList<>();
    List<String> right = Arrays.asList("a", "b", "c");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "b", "c");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeEmptyRight() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = new ArrayList<>();
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "b", "c");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeBothEmpty() {
    List<String> left = new ArrayList<>();
    List<String> right = new ArrayList<>();
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = new ArrayList<>();
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testFilter() {
    List<String> filter = Arrays.asList("Moon", "M0on");
    StringChecker moonChecker = new IsMoon();
    List<String> filtered = ListExamples.filter(filter, moonChecker);
    List<String> expected = Arrays.asList("Moon");
    assertEquals(expected, filtered);
  }

  @Test(timeout = 500)
  public void testFilterWithMultipleMoon() {
    List<String> filter = Arrays.asList("Moon", "M0on", "Moon");
    StringChecker moonChecker = new IsMoon();
    List<String> filtered = ListExamples.filter(filter, moonChecker);
    List<String> expected = Arrays.asList("Moon", "Moon");
    assertEquals(expected, filtered);
  }

  @Test(timeout = 500)
  public void testFilterWithNoMoon() {
    List<String> filter = Arrays.asList("M0on", "M00n");
    StringChecker moonChecker = new IsMoon();
    List<String> filtered = ListExamples.filter(filter, moonChecker);
    List<String> expected = new ArrayList<>();
    assertEquals(expected, filtered);
  }

  @Test(timeout = 500)
  public void testFilterWithEmptyList() {
    List<String> filter = new ArrayList<>();
    StringChecker moonChecker = new IsMoon();
    List<String> filtered = ListExamples.filter(filter, moonChecker);
    List<String> expected = new ArrayList<>();
    assertEquals(expected, filtered);
  }

}
```

Finally, here is the content of the `lib` directory:

```
hamcrest-core-1.3.jar
junit-4.13.2.jar files
```


Here are the commands needed to trigger the bug:

`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-filename`

It runs the `grade.sh` with the link to the repository as the argument.

In order to fix the bug, we must pass the name of the .java file in the `student-submission` file as an argument into the `TestListExamples.java` file. We must edit the `TestListExamples.java` file so that it can take a file name as the argument.  
