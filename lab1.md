Question 1: 
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
Here we are trying to change directory. But since 
we give it no arguments it changes to home directory

```
[user@sahara ~/lecture1]$ ls
Hello.java  messages  README
```
Here we are trying to list everything. But since
we give it no arguemnts is list all files in the 
current directory

```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cat
hello
hello
```
Here we are trying to use CAT, but we give it no 
arguments. Thus CAT is given no bevaior and does the default
which is repeating whatever the user inputs. The output is kindof
an error unless the default is what you want. 

--------------------------------------------------
Question 2:
```
[user@sahara ~/lecture1]$ cd messages
[user@sahara ~/lecture1/messages]$
```

Here we are trying to change directory to our 
arguments or messages

```
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  zh-cn.txt
```

Here we are trying to list everything in our 
arguments or messages

```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```

Here we are trying to use cat on the file but
since it a directory, cat gives us a messages 
that "Is a directory" as its running into an Error

--------------------------------------------------
Question 3:
```
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$
```

Here we are trying to change directory to our 
arguments or Hello.java, but we cant as it is 
not a directory. Thus it give us this error

```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```

Here we are trying to list everything in our 
arguments or Hello.java but since is just a single
single, it returns us with teh single file

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

Here we run CAT on our argument or Hello.java and it returns all the 
contents in the file
