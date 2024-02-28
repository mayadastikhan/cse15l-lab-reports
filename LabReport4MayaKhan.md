# Lab Report 4
## Vim
### Log into ieng6

<img width="786" alt="Screenshot 2024-02-27 at 4 04 40 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/904de535-03cb-41a8-9dcc-e2bbc87cc96f">

Keys Pressed: `ssh m7khan@ieng6.ucsd.edu` `<enter>`
* As I have previously generated my SSH keys for ieng6, no password was needed. Therefore, I only needed to enter the above keys to log in.

### Clone fork of the repository from Githib account

<img width="809" alt="Screenshot 2024-02-27 at 4 23 57 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/cab8e636-e75e-41e4-9b91-729320d24d14">

Keys Pressed: `cs15lwi24` `<enter>` `git clone` `<command>` `v`

* Before cloning the fork of the reposititory, I typed cs15lwi24 to begin working in ieng6. I had already copied the SSH url of the fork on GitHub, so ,to clone the fork, all I needed to do was type `git clone` and paste the SSH url which is `git@github.com:mayadastikhan/lab7.git`.

### Run the tests, demonstrating they fail

<img width="742" alt="Screenshot 2024-02-27 at 4 30 07 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/b0fb2477-3758-49c6-98c8-29714adf217f">

Keys Pressed: `cd` `<tab>` `<enter>` `sh` `<tab>` `t` `<tab>` `<enter>`

* Using `cd` and `<tab>` autofills `cd lab7/` as it is the only directory within the current working directory. When pressing `<enter>`, the dirctory changes to lab7 where we can run tests. Typing `sh` and then `<tab>` gives a list of options to run including `test.sh`. Now, all I need to add is `t` and then `<tab>` to autofill `test.sh`. Pressing `<enter>` runs the tests in the shell and produces the test failure.

### Edit code file to fix failing test

<img width="745" alt="Screenshot 2024-02-27 at 5 05 58 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/6ab99ba2-8519-4a97-a3ac-6de0504355e8">

<img width="676" alt="Screenshot 2024-02-27 at 5 05 22 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/d8c496fa-9cf6-473c-a504-3772ff8c0949">


Keys Pressed: `vim l` `<tab>` `.` `<tab>` `<enter>` `44G` `e` `x` `i` `2` `<esc>` `:x` `<enter>`
*`vim l` then pressing `<tab>` autofills `ListExamples` and adding `.` and pressing `<tab>` adds the `.java`. After pressing `<enter>`, VIM opens and `44G` takes the cursor straight to line 44 where the error appears. Then, pressing `e` takes the cursor to the end of the first word, which is the 1 in index1. The 1 is then deleted by pressing the key `x`. Using `i` to commence insert mode, the key `2` adds 2 to the place of the cursor, creating `index2`. `<esc>` exits insert mode and `:x` `<enter>` saves and exits VIM.

### Run the tests, demonstrating now they succeed

<img width="663" alt="Screenshot 2024-02-27 at 5 06 34 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/408a1d26-d9fd-44b5-a63a-26d829135f8c">

Keys Pressed: `<up>` `<up>` `<enter>`
* Using the bash history shortcuts, `<up>` `<up>` autofills `sh tests.sh` and `<enter>` runs the tests, which now successfully run.

### Commit and push the resulting change to your Github account

<img width="677" alt="Screenshot 2024-02-27 at 5 12 19 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/a491586d-a8dd-4e4e-9c5c-0d5fe97a07b8">

Keys Pressed: `git add .` `<enter>` `git commit -m "Fixed runtime error"` `<enter>`
* `git add .` stages the additons to the files and `git commit -m "Fixed runtime error"` commits the changes with the message in the command line argument, in this case: "Fixed runtime error", and pushes them to the main directory.

