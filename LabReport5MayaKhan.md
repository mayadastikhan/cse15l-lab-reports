# Lab Report 5 - Putting it All Together (Week 9)

## Part 1 – Debugging Scenario

### Lab 7 Bugs and Symptoms #888
```
Anonymous

Hello,
I have been having an ongoing issue in my ListExamples.java and I am not sure
what is wrong. I'm trying to implement a method merge in my ListExamples class
which should take two sorted lists of strings and return a new list containing
all the strings from both lists in sorted order. However, when I run my tests,
I'mmgetting a failure with an IndexOutOfBoundsException.

Here's a screenshot of the error message:

```
<img width="800" alt="Screenshot 2024-03-11 at 11 18 09 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/822871b1-240d-41cd-ac37-048a388f1439">

```
I think the bug might be related to how I'm iterating over the elements of the lists,
but I'm not entirely sure. Any help or suggestions would be greatly appreciated.
I have left the code below for you to checkout. Thank you!!


```


<img width="800" alt="Screenshot 2024-03-11 at 11 24 44 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/105fdcdd-f510-4018-b3ea-34462bc07883">


<img width="800" alt="Screenshot 2024-03-12 at 12 12 47 AM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/97519033-cf15-4fd8-a97a-591069f9cf38">

<img width="800" alt="Screenshot 2024-03-12 at 12 12 03 AM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/36187bc5-e535-4e7c-8b23-2808ee3a3824">

## 2 Answers
```
TA

Hi there,
Thanks for reaching out! The IndexOutOfBoundsException often occurs when trying to
access an index that is out of bounds of the list. It seems like your loop condition
might be causing the issue. Have you carefully considered how the loop condition should
be evaluated? It might be helpful to review the loop condition and ensure it's correctly
handling the cases when one of the lists is exhausted.

Let me know if you need further assistance!

```

```
Anonymous

Thanks for the suggestion! I've taken a closer look at the loop condition and printed out
some debug information to see what's happening. I ran some extra tests on the incrementation
of Index1 and Index2 and saw that my 1st while loop had incorrectly bounded index2 as it
exceeded the length of list2.

I changed the `||` to a '&&' in the first while loop. The tests now run smoothly.

```
<img width="800" alt="Screenshot 2024-03-12 at 12 06 16 AM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/14725f21-cc98-4918-9440-0f017c8ef6b9">

<img width="800" alt="Screenshot 2024-03-12 at 12 07 06 AM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/bb63d83c-d102-4e3a-b720-fcbcd37ab66d">


## Structure of lab7 directory
```
lab7/
│
├── src/
│   ├── ListExamples.java
│   └── ListExamplesTests.java
│
├── test.sh
│
└── README.md
```

## Part 2 - Reflection

Throughout the second half of this quarter, I have learned:

* Collaborative coding, including branching to not affect main code base. Committing and pushing work alongside this as I have hearned you can locally work on code and coommit and pish changes to local Git repositiories. Pull requests, additionally, push developers local branches to the cenral repository and merge after PRs go through with proper code review, collaboration, and feedback. These all combine into the multifaceted concept of collaborative coding. Throughout this process, effective communication among team members is essential. Git provides tools for managing conflicts, reviewing changes, and tracking the history of the codebase, enabling smooth collaboration even in distributed teams. 

* I have also learned a handful of useful commands used in terminal that assist in interacting with the operating system and navigating tasks more efficiently. Learning to write shell scripts allows users to automate complex workflows, saving time and effort in the long run. Also, Command-line tools often provide powerful debugging and troubleshooting capabilities. Overall, learning to work with command-line commands and arguments is an empowering skill that opens up a world of possibilities for efficiently managing and interacting with computer systems.


