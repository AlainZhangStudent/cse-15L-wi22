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

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport2/labs2s1.png)

The methods being called are ```main```, which runs the program, and ```handleRequest``` which handles the incoming HTTP requests. The relevant arguments for main are Strings[] args which represent the command line arguments, and the values of relevant fields are the port variable which is initialized based on the port number given in the args. The port variable is set to the integer value parsed from the command line. The relevant arguments for handRequest method are the URI url, type URI. and the field tracker accumulates the messages by users and errors. The field changes when something is posted to the url query and it gets appended to the tracker variable when using the right format. 

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport2/labs2s2.png)

Same explanation as above except in action, the tracker variable is tracking the messages inputted as shown in the image.

Part 2:

Here is the absolute path to the private key for the SSH key

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport2/absolutepath.jpg)

Here is the absolute path to the public key for the SSH key

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport2/absolutepathpublic.jpg)

Here is the terminal interaction where I login

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport2/sshlogin.jpg)

Part 3:

I learned something pretty cool about openssh protocols, specifically how private keys and public keys are like locks and keys that check if you have the right key for the ssh to the server. I didn't know the default was authentication_keys for the serverend and the private being in the .ssh directory.

