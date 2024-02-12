# Lab Report 3:

## Part 1: Bugs
* Failure Inducing Input for Buggy Program:
    * In `testAppend()`, the following code produces a failed test in Junit as it tests appending multiple elements to the LinkedList.
```
 @Test
    public void testAppend() {
        LinkedList list = new LinkedList();
        list.append(1);
        list.append(2);
        list.append(3);
        assertEquals("1 2 3 ", list.toString());
    }
```
* Non-failure Inducing Input for Buggy Program
    * As opposed to `testAppend()`, `testAppendOne()` only checks for adding one element via `append(int value)`
    * It only checks if the value of the first element, not any other node. This may allow bugs to be unchecked in the code.
    
```
@Test
    public void testAppendOne(){
        LinkedList list = new LinkedList();
        list.append(1);
        assertEquals("Check appending one element",
            1, list.first());
    }
```
* Symptoms of above output
    * testAppend() has the symptom `java.lang.OutOfMemoryError` at the `append(3)` at line 23 of the tester class.
    * testAppendOne(), as you can see on the left, passes the JUnit test with the indicated green check mark.
  
<img width="852" alt="Screenshot 2024-02-11 at 6 25 51 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/78b162d2-1a7d-4bf3-8383-50461ceaf3ee">


* Bug in append() before
    * There is a bug in the while loop `while(n.next != null)` that causes the loop to infinitely loop
    * Thus, the JVM is unable to continue to run the tester method due to insufficient space in the Java heap.
```
 public void append(int value) {
        if(this.root == null) {
            this.root = new Node(value, null);
            return;
        }
        // If it's just one element, add if after that one
        Node n = this.root;
        if(n.next == null) {
            n.next = new Node(value, null);
            return;
        }
        // Otherwise, loop until the end and add at the end with a null
        while(n.next != null) {
            n = n.next;
            n.next = new Node(value, null);
        }
    }
```

* Bug in append() after
    * The `n.next = new Node(value, null);` was included in the `while(n.next != null)` loop, leading there to be a java.lang.OutOfMemoryError.
    * This is a runtime error caused by an infinite loop which added multiple nodes with same value to the end of the list.
    * Since `Node n` was always set to `n.next = new Node(value, null);` in the while loop, the parameters of the while loop continuously loop as the next node is always Node n with the value of the parameter int value, not null.
    * Thus, adding `n.next = new Node(value, null);` after the while loop, loops through the nodes until the node previous of the tail node and adds the new node at the end of the list.
```
public void append(int value) {
        if(this.root == null) {
            this.root = new Node(value, null);
            return;
        }
        // If it's just one element, add if after that one
        Node n = this.root;
        if(n.next == null) {
            n.next = new Node(value, null);
            return;
        }
        // Otherwise, loop until the end and add at the end with a null
        while(n.next != null) {
            n = n.next;
        }
        n.next = new Node(value, null);
    }
```
 
    
