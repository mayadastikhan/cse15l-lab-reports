# Lab Report 2

## Part 1:
### ChatServer.java Code

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    private StringBuilder log = new StringBuilder();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Welcome to Maya's Chat Server");
        } 
        else if (url.getPath().contains("/add-message")) {
          String query = url.getQuery();
          if(query.startsWith("s=")) {
            String messageStr1 = query.split("=", 5)[1];
            String message = messageStr1.split("&")[0];
            String user = query.split("=", 5)[2];
            log.append(String.format("%s: %s\n", user, message));
            return log.toString();
          }
          else {
            return "/add-message requires a query parameter s\n";
          }
        }
        return "404 Not Found!";
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```


<img width="750" alt="Screenshot 2024-01-30 at 4 46 09 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/1612d212-02c2-4a8b-ab2b-784adf6f4d4c">

#### Which methods in your code are called?

* `handleRequests(URI url)` method in the Handle class is called, which is responsible for generating reponses to the url of the server according to the input of the user. It takes in the url "http://localhost:8888/add-message?s=Hello&user=mayakhan" and parses the url into path, query, and extra arguments to display the username and message added to the url.

* `main(String[] args)` method is called in the ChatServer class and intializes the Handler class with the port inputed by the user. The user inputs a port number into the command-line argument, in this scenario `8888`, and starts the server.

#### What are the relevant arguments to those methods, and the values of any relevant fields of the class?

* `handleRequests(URI url)` method has `URI url`, which is the parameter for the method passing the argument representing the URL of the server. In the case of this instance, the url passed as a parameter is "http://localhost:8080/add-message?s=Hello&user=mayakhan". `private StringBuilder log` is intialized to store the messages received by the server's url, thus acting as a field value in the method. `private StringBuilder log` appends the username and the message, "mayakhan: Hello". `String query`, ` String messageStr1`, `String message`, `String user` are all strings that hold values that have been extracted from the url to get the inputed username and message from the url.

* `main(String[] args)` method has the command-line argument `String[] args` passed to the method which carries the port number for the server. `int port` holds the integer of the port number inputed by the user. The port number is 8888 and is used to start the server. 

#### How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

* `log` field in the `Handler` class changes as messages are inputed to the url through the use of the path `/add-message`. In the case above, log contains no messages at the beginnning of `handleRequests(URI url)` method and accumulates "mayakhan: Hello". 
  

<img width="750" alt="Screenshot 2024-01-30 at 4 46 48 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/21864811-e1fa-4d51-99e4-c40114af379d">

#### Which methods in your code are called?
*`handleRequests(URI url)` method in the Handle class is called again, which takes in the url "http://localhost:8888/add-message?s=Hi there&user=ChatCPU" and extracts the url into query parameters if the user enters the path `/add-message`. The new message "ChatCpu: Hi there" is appeneded to log and returned. 


#### What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* `handleRequests(URI url)` method has `URI url` and takes in the updated url "http://localhost:8888/add-message?s=Hi%20there&user=ChatCPU". `log` contains the past messages inputed by the user, which in this case is "mayakhan: Hello". `String query`, ` String messageStr1`, `String message`, `String user` are all strings that hold values that have been extracted from the url to get the inputed username and message from the url.

#### How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

*`log` is changed once again after the if-else loops split the query and extract the username and message from the url. `String query`, `String messageStr1` , `String message` , `String user` are all given new field values as they take in the newly extracted query from the url. The new message "ChatCpu: Hi There" is appended to log and returned by the method. Thus, `log` now contains "mayakhan: Hello \n ChatCPU: Hi There". 


## Part 2: 

* The absolute path to the private key for your SSH key for logging into ieng6
`/Users/mayakhan/.ssh/id_rsa`

<img width="830" alt="Screenshot 2024-01-30 at 7 22 28 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/5f153565-4da9-4914-b887-d5b83f1c3614">

* The absolute path to the public key for your SSH key for logging into ieng6
`/Users/mayakhan/.ssh/id_rsa.pub`

<img width="830" alt="Screenshot 2024-01-30 at 7 22 28 PM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/035f7bdb-4853-418a-94d8-01c9cb619dc3">

*  A terminal interaction where you log into your ieng6 account without being asked for a password.
<img width="830" alt="Screenshot 2024-01-24 at 10 25 25 AM" src="https://github.com/mayadastikhan/cse15l-lab-reports/assets/151574602/58cdf173-96e2-434f-b60f-47af8ca021ab">


 ## Part 3:
### What I have learned:
 * In the past two weeks, I have learned how to log onto the remote server using `ssh` and `ieng6`. Additionally, I have learned more about URLs and their make-up such as path, query, and anchor.
 * Using what I have learned above has allowed me to also write my own web servers such as ChatServer.
 * I have also learned the difference between bugs and symptoms, and failure-inducing inputs.
