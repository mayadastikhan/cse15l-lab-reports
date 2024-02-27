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
        assertEquals("Check appending one element", 1, list.first());
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


   `[user@sahara ~/docsearch]$ grep -i "differential cytotoxicity" ./technical/*/*.txt`
      
      `
  
      ./technical/biomed/1471-2091-2-11.txt:          Differential cytotoxicity of glycine-conjugated

      `
  
    * The above output shows that case-sensitivity is ignored as `Differential cytotoxicity` is returned by the command with the string `differential cytotoxicity`.
  

  `user@sahara ~/docsearch]$ grep -i "Crypt abscess" ./technical/*/*.txt`

    ```
    
   ./technical/biomed/1471-230X-3-5.txt:        apoptosis, crypt abscess, and crypt loss has been
   ./technical/biomed/1471-230X-3-5.txt:        to confusion with 'crypt abscess' of inflammatory bowel
   ./technical/biomed/1471-230X-3-5.txt:        disease. 'Crypt abscess' and 'cryptitis' associated with
   ./technical/biomed/1471-230X-3-5.txt:          crypt abscess were defined respectively as infiltration
   ./technical/biomed/1471-230X-3-5.txt:        crypt abscesses in these reports, it is evident that the
   ./technical/biomed/1471-230X-3-5.txt:        lumina and suggested 'crypt abscess-like' changes [ 14 ] .
   ./technical/biomed/1471-230X-3-5.txt:        showed occasional crypt abscess (Table 2) and this may
   ./technical/biomed/1471-230X-3-5.txt:        damage [ 26 ] . Mild cryptitis with a few crypt abscesses
   ./technical/biomed/1471-230X-3-5.txt:        and crypt abscesses with infiltration of crypt lining and
   ./technical/biomed/1471-230X-3-5.txt:        diagnosis of A-GVHD. Cryptitis and crypt abscesses are not
    
    ```
   * The above output displays how -i prints the string ignoring case-sensitivity as both `Crypt abcess` and `crypt abcess` is outputted.
      
### `grep -m NUM, --max-count=NUM`
* puts NUM integer of the maximum count of lines returned and grep stops outputting after NUM of matched lines in each file have been printed


   `[user@sahara ~/docsearch]$ grep -m 1 "glycosylphosphatidylinositol" ./technical/*/*.txt`


    ```
       
   ./technical/biomed/1471-2121-3-11.txt:        this glycosylphosphatidylinositol anchored glycoprotein on
   ./technical/biomed/1471-2121-3-8.txt:        also known to be a glycosylphosphatidylinositol
   ./technical/biomed/1471-213X-3-2.txt:        glycosylphosphatidylinositol (GPI)-linked and a 32 kDa
   ./technical/biomed/1471-2164-4-25.txt:        via a glycosylphosphatidylinositol anchor into the cytosol
    ```
    * Each file containing `glycosylphosphatidylinositol` can only print 1 matched line due to the NUM integer 1 following the command `grep -m`.


  `[user@sahara ~/docsearch]$ grep -m 2 "glycosylphosphatidylinositol" ./technical/*/*.txt`

    ```
    
   ./technical/biomed/1471-2121-3-11.txt:        this glycosylphosphatidylinositol anchored glycoprotein on
   ./technical/biomed/1471-2121-3-8.txt:        also known to be a glycosylphosphatidylinositol
   ./technical/biomed/1471-2121-3-8.txt:        glycosylphosphatidylinositol (GPI)-anchored receptor for
   ./technical/biomed/1471-213X-3-2.txt:        glycosylphosphatidylinositol (GPI)-linked and a 32 kDa
   ./technical/biomed/1471-2164-4-25.txt:        via a glycosylphosphatidylinositol anchor into the cytosol
    ```

    * As shown above, changing the command line argument NUM to 2 has increased the amount of lines by 1 because `./technical/biomed/1471-2121-3-8.txt` contains at least 2 matched lines with `glycosylphosphatidylinositol`. If there are more than 2 lines matching, they will not print because the max is set to 2.
    
    

### `grep -v, --invert-match`
* returns the lines that do not contain the string in the command-line argument

  
   `[user@sahara ~/docsearch]$ grep -vm 1  "The" ./technical/*/*.txt`


    ```
    
   ./technical/911report/chapter-10.txt:
   ./technical/911report/chapter-11.txt:
   ./technical/911report/chapter-12.txt:
   ./technical/911report/chapter-13.1.txt:
   ./technical/911report/chapter-13.2.txt:
   ./technical/911report/chapter-13.3.txt:
   ./technical/911report/chapter-13.4.txt:
   ./technical/911report/chapter-13.5.txt:
   ./technical/911report/chapter-1.txt:
   ...
   ```
    * The above output combines -v and -m to return the first line in each files in ./technical/ that does not contain `The`. Thus, the output goes on until each file that has a line without `The` is printed. The output appears to be empty because the first line without `The` in many of the files is an empty line.


   `[user@sahara ~/docsearch]$ grep -vi  "t" ./technical/911report/chapter-10*.txt`

    ```
    

    
        
            
            
                   days, if necessary.
            
            
            
            
    ...  
    ```
    * The above output shows a small section of output that the command `grep -vi "t"` for the single file `./technical/911report/chapter-10*.txt` produces. It finds all lines in `./technical/911report/chapter-10*.txt` that do not contain `t`, excluding case sensitivity. For the most part, it returns empty lines and the end of paragraphs.

### `grep -L, --files-without-match`
* returns the files that do not contain the string in the command line argument.

  
   `[user@sahara ~/docsearch]$ grep -L  "White House" ./technical/911report/chapter-*.txt`
  ```
     
   ./technical/911report/chapter-2.txt
   ./technical/911report/chapter-9.txt
  ```
    * The above output shows the paths to the two files ` ./technical/911report/chapter-2.txt` and `./technical/911report/chapter-9.txt`, which are shown to not have contained the string `White House`.


   `[user@sahara ~/docsearch]$ grep -Li  "pentagon" ./technical/911report/*.txt`
   
  ```
   ./technical/911report/chapter-13.3.txt
   ./technical/911report/chapter-2.txt
   ./technical/911report/chapter-8.txt
   ./technical/911report/preface.txt
   ```
  * The above command returns the text files in the `./technical/911report/` path that do not contain the word `pentagon`, ignoring case-sensitivity.
    
### The grep commands researched above were obtained by https://linuxcommand.org/lc3_man_pages/grep1.html

  
 
    
