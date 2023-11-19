Step 4: I started by logging into ieng6 using the command: `ssh cs15lfa23qo@ieng6.ucsd.edu`

Output: 
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/bbdd89fb-f76f-4f74-b366-51a2944c7090)


Step 5: I then cloned the fork of the repository from my Github account using the SSH URL. This was done with the command: `git clone git@github.com:UKCSE15L/lab7.git`

Output: 
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/66684a77-0ff1-4b7c-a734-b86fc57f8869)

Step 6: I then ran the tests using the command `bash test.sh`

Output:
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/b9b84bcc-3274-404e-8b45-6bdaaf409c00)

Step 7: To edit the code, I first opened the `ListExamples.java` file in vim using the command `vim ListExamples.java`

Output: 
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/7ec143ce-528f-4803-92f9-24d24b47a181)

I then input the following keys: `<down><down><down><down><right><right><right><right><right><right><right><x><i><2><esc><:wq><enter>`

This moves the cursor down from the starting position and to the right until it is on top of the `1` we want to remove. `x` then removes the `1` and `i` enters insert mode. `2` next inserts a `2` where the `1` was before. `esc` returns us to normal mode. `:wq` saves and quits the file. Then, pressing the `enter` key exeuted the `:wq` command and succesfully exited the file.

Here is the corrected code:
![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/8bfef72e-d1a3-46c9-9382-f7173a0d6a2d)

I then did `ctrl-R` and typed `bash` and then hit enter which ran the `bash test.sh` command from earlier.
