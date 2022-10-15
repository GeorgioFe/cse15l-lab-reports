# Lab Report 2 - Servers and Bugs

## Part 1
&emsp; In this part we are going to showcase our work on the Simple Search Engine that we built.

### &emsp; Code:

<code>

    import java.io.*;
    import java.net.URI;
    import java.util.*;

    class Handler implements URLHandler {
        // The one bit of state on the server: a number that will be manipulated by
        // various requests.
        ArrayList<String> words = new ArrayList<String>();

        public String handleRequest(URI url) {
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    words.add(parameters[1]);
                    return String.format("Added to the list: %s", parameters[1]);
                }
            }

            else if (url.getPath().contains("/search")) {
                String[] parameter = url.getQuery().split("=");
                if (parameter[0].equals("s")) {
                    String input = parameter[1];
                    String results = "";
                    for (int i = 0 ; i < words.size(); i++) {
                        if (words.get(i).contains(input)) {
                            results = results + words.get(i) + " ";
                        }
                    }

                    if (results == ""){
                        return String.format("Nothing Found!");
                    }
                    else {
                        return String.format("Search results: %s", results);
                    }
                }
        
            }
            return "404 Not Found!";
        }
    }


    public class SearchEngine {
        public static void main(String[] args) throws IOException {
            if(args.length == 0){
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }

            int port = Integer.parseInt(args[0]);

            Server.start(port, new Handler());
        }
    }
</code>

### &emsp; Missing Port Number:
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-1.png)

&emsp; In this case, we forgot to add the port number when running, so the program couldn't call the handleRequest() method, which is in the Handler class.

### &emsp; Missing Path and/or Query:
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-2.png)

&emsp; In this case, we forgot to add a path and a query in the url, so the program couldn't decide what to do, so we printed an error message.

### &emsp; Adding a String:
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-3.png)

&emsp; Here, we added the path "/add" and the query "?s" and added the word "test" to the list. In this case, the handleRequest() method was called with the parameter being the url. The program figured out that the "/add" path was there and returned the output based on that.

Other Examples of Adding:

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-4.png)

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-5.png)

### &emsp; Querying a String:
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-6.png)

&emsp; Here, we added the path "/search" and the query "?s" and searched for the word "te". In this case, the handleRequest() method was called with the parameter being the url. The program figured out that the "/search" path was there and returned the output based on that.

Other Examples of Querying:

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-7.png)

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-8.png)

---

## Part 2
&emsp; For this part, we are going to choose two of the bugs from different files (lab 3 repo) and for each, show the failure-inducing input (the code of the test), the symptom (the failing test output), The bug (the code fix needed), and then, explain the connection between the symptom and the bug. Why does the bug cause that particular symptom for that particular input?

### &emsp; Bug #1:

&emsp; Failure-inducing Input
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-9.png)
&emsp; *As we see, the failure-inducing input in this case is the array input1.*


&emsp; Symptom
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-10.png)
&emsp; *The symptom for this code is the discrepancy between the actual output at element [0], which is 0, and the expected output, 6.*


&emsp; The Bug
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-11.png)
&emsp; *The bug is that the method is updating the current array instead of the newly initialized array (newArray) and is returning the input array (arr), instead of newArray.*

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-12.png)
&emsp; *Fixed code.*


### &emsp; Bug #2:

&emsp; Failure-inducing Input
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-13.png)
&emsp; *As we see, the failure-inducing inputs in this case are the ints 1, 2, and 3 into the attend() method.*


&emsp; Symptom
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-14.png)
&emsp; *The symptom for this code is the OutOfMemoryError, which is caused by the program going into an infinite loop.*


&emsp; The Bug
![image](../Screenshots/Lab%20Report%202/lab2-screenshot-15.png)
&emsp; *The bug is that the method is assigning a new node for each next pointer instead of reaching to the end of the list, and then assigning a new node to the last next pointer, once.*

![image](../Screenshots/Lab%20Report%202/lab2-screenshot-16.png)
&emsp; *Fixed code.*