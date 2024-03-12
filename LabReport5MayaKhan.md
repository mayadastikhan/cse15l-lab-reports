# Lab Report 5 - Putting it All Together (Week 9)

## Part 1 – Debugging Scenario

### Lab 7 Bugs and Symptoms #888
```
Anonymous

Hello,
I have been having an ongoing issue in my ListExamples.java and I am not sure what is wrong. I'm trying to implement a method merge in my ListExamples class which should take two sorted lists of strings and return a new list containing all the strings from both lists in sorted order. However, when I run my tests, I'm getting a failure with an IndexOutOfBoundsException. Here's a screenshot of the error message:

```
<img width="800" alt="Screenshot 2024-03-11 at 11 18 09 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/822871b1-240d-41cd-ac37-048a388f1439">

```
I think the bug might be related to how I'm iterating over the elements of the lists, but I'm not entirely sure.
Any help or suggestions would be greatly appreciated. I have left the code below for you to checkout. Thank you!!


```


<img width="800" alt="Screenshot 2024-03-11 at 11 24 44 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/105fdcdd-f510-4018-b3ea-34462bc07883">


## 1 Answer
```
TA

Hi there,
Thanks for reaching out! The IndexOutOfBoundsException often occurs when trying to access an index that is out of bounds of the list. It seems like your loop condition might be causing the issue. Have you carefully considered how the loop condition should be evaluated?

It might be helpful to review the loop condition and ensure it's correctly handling the cases when one of the lists is exhausted.

Let me know if you need further assistance!

```
