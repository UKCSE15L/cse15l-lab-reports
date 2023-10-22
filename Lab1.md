# 1.  `cd` with no arguments:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/f960af1e-a09f-4b2a-9993-64ddcfe19716">

I started with the working directory at the lecture1 folder. When I ran `cd` with no argument, the working directory was switched over to `/home` by default. I do not believe that this is an error and more of an intentional design decision.

# 2.  `cd` with path to a directory as the argument:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/51e0e7b0-5767-4a53-bcd0-173a7e2e3cbf">

I started with the working directory at the home directory. When I ran `cd` with a path to a directory as the argument, the working directory was switched to the `/lecture1` directory as I expected. This is not an error as the command ran as intended.

# 3.  `cd` with path to a file as the argument:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/4ad1bc9a-cc9e-4975-b425-d1663b211dd1">

I started with the working directory at the `/home` directory. When I ran `cd` with a path to a file as the argument, I received an error message claiming that the path I provided wasn't to a directory. This output is not an error as I received an appropriate message describing what went wrong. But `cd` is not intended to be used with paths to files as arguments.  

# 4.  `ls` with no arguments:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/96fde35c-4044-4c08-9e31-d17b4f65dd7c">

I started with the working directory at the `/home` directory. When I ran `ls` with no argument, it printed out the `lecture1` directory as I would have expected. This is not an error since the command functioned as it would have if I had put my working directory as the argument.

# 5.  `ls` with path to a directory as the argument:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/1dda3e20-b03a-4e2b-8b3d-9006d558a0be">

I started with the working directory at the `/home` directory. When I ran `ls` with a path to the `lecture1` directory as the argument, it printed out the files under `lecture1` as I would expect. This is not an error since the command had the expected output

# 6.  `ls` with path to a file as the argument:
<img width="504" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/9190fcbd-bb3e-4b9b-b8d3-97003e4f52af">

I started with the working directory as the `/home` directory. When I ran `ls` with a path to the `Hello.class` file as the argument, It printed out the path that I input. This seems to be an error since it shouldn't print anything at all since there are no files or directories under the file that I provided.

# 7.  `cat` with no arguments:
<img width="200" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/aba9065a-cb66-4faa-a578-5062395ee592">

I started out with the working directory as the `/home` directory. When I ran `cat` with no arguments, the program just stopped working entirely. I was able to type whatever I wanted and had to forcefully make a new terminal. This was definitely an error since the program stopped working.

# 8.  `cat` with path to a directory as the argument:
<img width="337" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/73030913-adb5-4e81-8c33-e5397e17231e">

I started out with the working directory as the `/home` directory. When I ran `cat` with a path to a directory as the argument, I receieved this output. The command functioned as intended and printed out an accurate message. This is not an error.

# 9.  `cat` with path to a file as the argument:
<img width="916" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/6ada0461-b51e-4cb6-b677-3e5cfae60457">

I started out with the working directory as the `/home` directory. When I ran `cat` with a path to a file as the argument, I received this output. I am sure that this is an error but do not know why this specific message was output.
