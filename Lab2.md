**Part 1**

```import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler 
{
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    int num = 0;
    String holder = "";

    public String handleRequest(URI url) {

            if (url.getPath().contains("/add-message")) 
            {
                num += 1;
                String[] parameters = url.getQuery().split("=");

                holder += num + ". " + parameters[1] + "\n";

                return holder;
            }
            return "404 Not Found!";
    }
}

class StringServer 
{
    public static void main(String[] args) throws IOException 
    {
        if(args.length == 0)
        {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
The above is the code for my StringServer. 

Here are two examples of me using /add-message. The first had the query ?s=Hello, and the second had the query ?s=Hello Again!

![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/3610d236-91b9-4646-a491-226fbfa14a6e)

![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/0525b764-5930-41eb-a9f5-23041cf99946)

For both examples, the `handleRequest` method was called to return the updated String which would then be printed to the screen. 

The 'handleRequest' method has a single argument, 'URI url', which is used to store the URL passed to this method. This URL is then processed inside the method to perform specific actions based on its path and query parameters.

The relevant fields of the `Handler` class are the `num` integer which is incremented with every call and the `holder` String which is concatenated with every call with the newest string.

For both of these requests, the `num` is incremented and the `holder` String is concatenated with the newest String and a newline added to the end of it.


**Part 2**

<img width="319" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/a6526be6-6380-47a0-83dd-8dff626129eb">

The absolute path to the private key would be /Users/umark/.ssh.id_rsa

The absolute path to the public key would be /Users/umark/.ssh.id_rsa.pub

Here is me logging in with no password:
<img width="759" alt="image" src="https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/fd9d587a-f51e-4072-b442-a137ec2bc49b">


**Part 3**

Most of what we've learned these past two weeks have been new to me. How to connect to a remote server, how to build a local server, how to navigate VSCode, how to set up SSH Keys, and I also learned how to connect to a vpn to access the UCSD servers from home. All of this information is new to me.
