# Milan Suresh Lab Report 2 - Servers and SSH Keys

# Part 1

In this part, we will be creating a web server called ChatServer. This ChatServer calls upon the Server.java file used previously in this class. Attached below is the code:

```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    // Saves messages in ArrayList
    ArrayList<String> messages = new ArrayList<String>();
    

    public String handleRequest(URI url) {
        //if there is no request to add messages, return all the previous messages
        if (url.getPath().equals("/")) {
            return this.printMessages();
        } else if (url.getPath().equals("/add-message")) {
            //figures out the message from the query and adds it to the arraylist
            String[] parameters = url.getQuery().split("=");
            String[] firstArg = parameters[1].split("&");
            String current = "";
            current+=parameters[2]+": " + firstArg[0];
            current+="\n";

            messages.add(current);
            //return all messages
            return this.printMessages();
        } else {
            //if the url is invalid, return an error
            return "404 Not Found!";
        }
    }

    public String printMessages(){
        //iterates through the messages ArrayList and adds them to total String
        String total="";
        for (int x = 0; x< messages.size();x++ ){
            total+=messages.get(x);
        }
        //returns total String
        return total;
    }
}

    

class ChatServer {
    public static void main(String[] args) throws IOException {
        //checks if port number not there
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        
        //starts server
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```
Now, let's use add-mesage to add some messages.

<img width="1440" alt="Screenshot 2024-01-30 at 11 17 43 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/32e4b2fb-4cdd-4bf4-8bf2-b4112a8e0af2">

Our query was specified with `/add-message?s=Hello World&user=HumanBoy`. A `parameters` array (`"s"`,`"Hello World&user"`,`"HumanBoy"`) is created by splitting the query with `"=`, and the `firstArg` array is created by splitting the first argument of `parameters` with `&` (`"Hello World"`, `"user"`).

`String current` is created to hold the message. `current+=parameters[2]+": " + firstArg[0];` adds the formatted message, `"HumanBoy: Hello+World"`. Later, `current+="\n";` adds the line skip. Later `messages.add` is called with the argument of `current`. Then, we call `this.printMessages` to print all the messages so far.

<img width="1438" alt="Screenshot 2024-01-30 at 11 18 19 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/966087ae-2e9d-46b3-9fd1-b60682bae98e">

Our query was specified with `/add-message?s=Hola, amigos&user=Diego`. A `parameters` array (`"s"`,`"Hola, amigos&user"`,`"Diego"`) is created by splitting the query with `"=`, and the `firstArg` array is created by splitting the first argument of `parameters` with `&` (`"Hola, amigos"`, `"user"`).

`String current` is created to hold the message. `current+=parameters[2]+": " + firstArg[0];` adds the formatted message, `Diego: Hola,+amigos`. Later, `current+="\n";` adds the line skip. Later `messages.add` is called with the argument of `current`. Then, we call `this.printMessages` to print all the messages so far.

# Part 2

<img width="454" alt="Screenshot 2024-01-30 at 11 45 50 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/66cf1c9f-f9e3-446d-bf71-56bd088aeb4f">

<img width="630" alt="Screenshot 2024-01-30 at 11 46 49 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/c178a6db-47c3-4222-8f37-00cb60bedd84">


<img width="469" alt="Screenshot 2024-01-30 at 11 47 37 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/307e8760-6ea2-4fa4-b836-a03c8f9a4a40">



# Part 3

In this report, I learned how to work with URLs and put text onto a server. Previously, we used code that was given to us, but I think that by re-implementing a lot of it myself, I was forced to learn how to work with URLs.
