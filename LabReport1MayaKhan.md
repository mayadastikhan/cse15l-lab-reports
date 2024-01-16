# Lab Report 1


## 1. Share an example of using the command with no arguments.

   
### cd: 

<img width="950" alt="Screenshot 2024-01-15 at 8 14 07 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/36a9032a-5a8b-40d2-88ff-910d9956aa1f">
The working directory is /home and displays no output when cd is entered without an argument. This is due to the fact that the current working directory is /home, thus there is no directory to change to on the path before home or one stated as the argument. The output is not an error because the user stays in the home directory, which is expected when cd is followed without any argument.


### ls:     

<img width="950" alt="Screenshot 2024-01-15 at 8 14 23 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/d3df350f-f0f9-41c5-b24d-3521c16c9a8e">
The working directory is /home and the output from this command is "lecture1  messages", listing the files and folders in the given path. This is not an error as the terminal correctly registers the files and folders within /home.

### cat:

<img width="950" alt="Screenshot 2024-01-15 at 8 14 55 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/f63fb7e7-f18c-4b92-ad6c-adbcf898d241">
The working directory is /home and the output is a loop that duplicates the user-inputed string. As shown above, "hi" is replicated. The output is an infinite loop, therefore, ctrl + C is used to break the loop. This could be considered a logical error since it is an infinite loop, however, the command cat takes standard input and transforms it into output. Therefore, the output of the cat command wihout any argument is not an error.


## 2. Share an example of using the command with a path to a directory as an argument.

### cd:

<img width="950" alt="Screenshot 2024-01-15 at 7 31 28 PM"
src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/b123901b-84b7-479b-80a8-56bf76faef70">


The working directory changes from /home to /home/lecture1 from the above command. This is because the argument 'lecture1' has the command cd change the current working directory to the path of the folder 'lecture1'. This is not an error because the command correctly executes the change of directories as seen by the '[user@sahara ~/lecture1]$' outputed after the command is executed.



### ls:

![Screen Shot 2024-01-11 at 5 31 12 PM](https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/4829f48e-9233-4e34-923e-34182b730b81)


The working directory is /home and, using the argument of 'lecture1', the output is 'Hello.class  Hello.java  messages  README', listing all the files and folders within the lecture1 file. The working directory still remains as /home after the command is executed and no error is outputed. However, if the working directory were to be home/lecture1, there would be an error outputed saying "ls: cannot access 'lecture1': No such file or directory". This is due to the fact that ls can only list files and folders within the current working directory and lecture1 cannot be listed within itself.

### cat:

![Screen Shot 2024-01-11 at 5 32 56 PM](https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/660d4a2b-11f4-4975-849b-39144829f75c)


The working directory is home/ and the output of the command with the argument 'lecture1' is 'cat: lecture1: Is a directory'. When the argument is a directory, the command cat will output whether or not it is a directory within the current path. This output is not an error since 'lecture1' is a directory within the current working directory. For example, if the working directory were to be home/lecture1 with the same argument 'lecture1', then the output would be 'cat: lecture1: No such file or directory' because the command cannot execute using the parent directory.


## 3.Share an example of using the command with a path to a file as an argument.

   
### cd:

![Screen Shot 2024-01-11 at 5 41 08 PM](https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/180dba36-644c-4e38-9850-ff9706ee2e10)


The working directory is home/ and, when the argument is a path to a file, the output is 'bash: cd: lecture1/messages/en-us.txt: Not a directory'. This is because the cd command must refer to a directory explicitly because the argument must input where the path will change to. This is an error because the path to a file is not a parameterized argument and, additionally, a file cannot be an argument for the cd command because it is not a directory. If the working directory were to be home/lecture1/messages and the argument was en-us.txt, this would still produce an error because en-us.txt is a file.


### ls:

![Screen Shot 2024-01-11 at 5 38 31 PM](https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/c5b3ea0b-5b1a-468f-9403-4474f2c7d0b4)



The working directory is home/ and, when the argument is 'lecture1/messages/en-us.txt', the output is 'lecture1/messages/en-us.txt'. The ls command with a path to a file as an argument will output the relative path to the file because there are no files or directories within a file to list. If the absolute path is used as an argument for the ls command, there will be an error as the argument can only be a relative path to the working directory.                                   


### cat:

![Screen Shot 2024-01-11 at 5 41 21 PM](https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/801e6576-3dc9-4e06-94c2-eba740f3687d)


The working directory is home/ and cat with the argument of a path to a file 'lecture1/messages/en-us.txt' will output 'Hello World!", which are the contents of the file the argument references. This is due to the fact that cat will print the contents of files given by the path in the argument. If there were to be two arguments of paths to files, then the command cat would concatentate the contents of both files. For example, the argument 'lecture1/messages/en-us.txt lecture1/messages/es-mx.txt' would output:

Hello World!
¡Hola Mundo!

