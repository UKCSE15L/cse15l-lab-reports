**Part 1**

Student: "Hello, I am a normal student writing an EdStem post as I need help debugging my program. I am having some trouble with my autograder, particularly one of the repositories from week 6 is causing me great trouble and anguish! My `grade.sh` bash script runs perfectly for all of the repositories except for the `list-methods-filename` repository. I know that this repository, which is my failure-inducing input, has the wrong name for the java file, but do not know what else to do or where to start debugging! I am totally freaking out, please help! I am including the terminal output which contains the symptom of the bug down below. Please help me TA, you are my only hope!" 

<img width="808" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/6f3c6397-75ef-4b5c-944d-7a296df1d57e">



TA (Teaching Assistant): "Yo what is up normal student, I am a totally normal TA or Teaching Assistant, have no fear as it is my duty to help you along the debugging process. Looking at the symptom you provided, it appears that there is not a problem in the `grade.sh` script at all. It looks like the error may actually be in the `TestListExamples` class! If you look closely at the stack trace, you can clearly see that all of the errors are in lines that reference the `ListExamples` java file. If you look even closer, you may notice that the same error is being repeated, the symbol cannot be found. Maybe start your debugging in the `TestListExamples` class, you mentioned that the provided repository uses a different name for the java file, perhaps the error has something to do with that."


Student: "Wow, thank you for the response! After looking into the `TestListExamples` class, I realized that all of the test methods were hard-coded to work on the `ListExamples` java file, but there were no measures to account for if that file didn't exist or went by a different name. Including a screenshot below of some of the test methods so you can get a general idea."

<img width="531" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/ff80153d-0e8e-4fb1-9d59-c2aa6ecd5df7">

That concludes the EdStem portion of my lab report.

The File and Directory structure needed to run 
