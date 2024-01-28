Part 1:

This is the code for ChatServer.java

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String tracker = "Hello World\n";
    public String handleRequest(URI url) {
        String query = url.getQuery();
        if (url.getPath().equals("/")) {
            tracker += "Type something \n";
            return tracker;
        } 
        else if (url.getPath().equals("/add-message")) {
            if(query.startsWith("s=")) {
                String getMessageUser = query.split("s=")[1];
                String getMessage = getMessageUser.split("&user=")[0];
                String getUser = getMessageUser.split("&user=")[1]; 
                tracker += getUser + ": " + getMessage + "\n";
            }
            else {
                tracker += "error \n";
            }
            return tracker;
        } 
        /*else {
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("count")) {
                    num += Integer.parseInt(parameters[1]);
                    return String.format("Number increased by %s! It's now %d", parameters[1], num);
                }
            }
            return "404 Not Found!";
        }*/
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
2 screenshots using /add-message

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport1folder/ls.png)


Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.


![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport1folder/ls.png)


Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

Part 2:

Here is the absolute path to the private key for the SSH key

Here is the absolute path to the public key for the SSH key

Here is the terminal interaction where I login


Part 3:

I learned something pretty cool about openssh protocols, specifically how private keys and public keys are like locks and keys that check if you have the right key for the ssh to the server. I didn't know the default was authentication_keys for the serverend and the private being in the .ssh directory.

