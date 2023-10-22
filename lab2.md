#Question 1: 

##StringServer.class

```
package wavelet;
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String text = "";
    int num = 0;
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return text;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                System.out.println(parameters[0]);
                if (parameters[0].equals("s")) {
                    num ++;
                    text += String.format("%d. ", num) + parameters[1] + "\n";
                    return text;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
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

![Image](Add1.png)
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
/home/lecture1

Here we are trying to change directory. But since 
we give it no arguments it changes to home directory

This one is not an error. 
```
[user@sahara ~/lecture1]$ ls
Hello.java  messages  README
```
/home/lecture1

Here we are trying to list everything. But since
we give it no arguemnts is list all files in the 
current directory

This one is not an error. 
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cat
hello
hello
```
/home/lecture1

Here we are trying to use CAT, but we give it no 
arguments. Thus CAT is given no bevaior and does the default
which is repeating whatever the user inputs. 

The output is kindof as its giving us the default rather 
then what we would usually need

--------------------------------------------------
Question 2:
```
[user@sahara ~/lecture1]$ cd messages
[user@sahara ~/lecture1/messages]$
```
/home/lecture1

Here we are trying to change directory to our 
arguments or messages

This one is not an error. 
```
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  zh-cn.txt
```
/home/lecture1

Here we are trying to list everything in our 
arguments or messages

This one is not an error. 
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```
/home/lecture1

Here we are trying to use cat on the file but
since it a directory, cat gives us a messages 
that "Is a directory".

This is giving us an error as we are tring to run Cat
on a directory rathet then file. 

--------------------------------------------------
Question 3:
```
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$
```
/home/lecture1

Here we are trying to change directory to our 
arguments or Hello.java, but we cant as it is 
not a directory. 

Thus it is a error since we are tring to change
directory to a file. 
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
/home/lecture1

Here we are trying to list everything in our 
arguments or Hello.java but since is just a single
single, it returns us with teh single file

This one is not an error. 
```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharse
ts.UTF_8);    
    System.out.println(content);
  }
}[user@sahara ~/lecture1]$
```
/home/lecture1

Here we run CAT on our argument or Hello.java and it returns all the 
contents in the file

This one is not an error. 
