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


<img width="882" alt="Screenshot 2024-02-11 at 6 25 51 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/90c1754e-f5bb-4e82-b429-7dce2ef5a2ba">


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

## Part 2: Researching Commands: grep

### `grep -i, --ignore-case`
* igores case-sensitivity when matching lines and finding patterns of the instance of the string
    * `grep i- "hello" ./commands/greetings*.txt`
      
      ```
      hello people
      Hello world
      ```
    *`grep -i "hello" ./commands/greetings*.txt`

    ```
    HELLO
    HeLlO
    hello
    Hello
    ```
### `grep -m NUM, --max-count=NUM`
* puts NUM integer of the maximum count of lines returned and grep stops outputting after NUM of matched lines have been printed
    * `grep -m 3 "hello" ./commands/greetings*.txt`


    ```
    hello!
    hello all:)
    hello, world
    ```


    * `grep -im  3 "hello" ./commands/greetings*.txt`

    ```
    HELLO
    hello!
    Hello, world
    ```
    
    

### `grep -v, --invert-match`
* returns the lines that do not contain the string in the command-line argument
    *`grep -v "hello" ./commands/greetings*.txt`


    ```
    Hello
    Hi
    Hiya
    Hola
    ```
    *`grep -iv "hello" ./commands/greetings*.txt`

    ```
    Hi
    Hiya
    Hola
    ```
  
 
    
