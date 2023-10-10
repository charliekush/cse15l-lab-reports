# cd Commands
## Command with no arguments
* Command: `cd`
* Current Working Directory: `/home/`
* Output:
```
[user@sahara ~]$ cd
[user@sahara ~]$ 
```
* Explanation: `cd` woth no arguements sets the current directory to the `/home/`
* Is error?: No
## Command with with a path to a directory as an argument
* Command: `cd lecture1`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ 
```
* Explanation: it moves the terminals CWD to `/home/lecture1`
* Is error?: No
## Command with a path to a file as an argument
* Command: `cd lecture1/Hello.java`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ cd lecture1/Hello.java
bash: cd: lecture1/Hello.java: Not a directory
[user@sahara ~]$ 
```
* Explanation: It searched for a the directory `/home/lecture1/Hello.java` and could not find it.
* Is error?: Yes, because `lecture1/Hello.java` and `lecture1/Hello.java` is a file
# ls Commands
## Command with no arguments
* Command: `ls`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ 
```
* Explanation: The command printed a list of files in the current directory `/home/`
* Is error?: No
## Command with with a path to a directory as an argument
* Command: `ls lecture1`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~]$ 
```
* Explanation: The command printed a list of files in the current directory `/home/lecture1`
* Is error?: No
## Command with a path to a file as an argument
* Command: `ls lecture1/Hello.java`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ ls lecture1/Hello.java
lecture1/Hello.java
[user@sahara ~]$ 
```
* Explanation: Because when `ls` is passed a file, it returns the path to the file.
* Is error?: No
# cat Commands
## Command with no arguments
* Command: `cat`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ cat
```
* Explanation: Nothing is printed because cat needs the path to a file. Because no arguement is passed, it waits for a file to be inputed.
* Is error?: No
## Command with with a path to a directory as an argument
* Command: `cat lecture1`
* Current Working Directory: `/home/`
* Output: 
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
[user@sahara ~]$ 
```
* Explanation: It searched for a the file `/home/lecture1` and could not find it.
* Is error?: Yes, because cat requires a directory to a file to be passed as an arguement.
## Command with a path to a file as an argument
* Command: `cat lecture1/Hello.java`
* Current Working Directory: `/home/`
* Output: 
```

[user@sahara ~]$ cat lecture1/Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOE
xception {
    String content = Files.readString(Path.of(args[
0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}[user@sahara ~]$

```
* Explanation: cat outputs the contents of the file at `lecture1/Hello.java`
Is error?: No
