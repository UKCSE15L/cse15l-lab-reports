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

Here are two examples of me using /add-message. The first had the query 

![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/3610d236-91b9-4646-a491-226fbfa14a6e)

![image](https://github.com/UKCSE15L/cse15l-lab-reports/assets/147003715/0525b764-5930-41eb-a9f5-23041cf99946)

