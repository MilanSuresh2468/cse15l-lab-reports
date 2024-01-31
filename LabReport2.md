# Milan Suresh Lab Report 2 - Servers and SSH Keys

# Part 1

`import java.io.IOException;
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
            System.out.println(parameters[1]);
            System.out.println(firstArg[0]);
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
`