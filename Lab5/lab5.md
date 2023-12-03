# Original Post by Student

Title: Issue with Java Program Output

Hi everyone,

I'm having a strange issue with my Fiboncci.java program. I'm supposed to print the Fibonacci sequence up to a given number, but I am getting this strange error. I am not sure what I did wrong. 

Here's a screenshot of the error when I run my unit tests:

![Image](error1.png)

(lines omitted) 

![Image](error2.png)

I have also attached all the files I have been working on. 



* Fibonacci.java
```
public class Fibonacci {
    public static int fib(int n) {
        if (n == 0)
            return 0;
        else
            return fib(n-1) + fib(n-2);
    }
}
```

* FibonacciTests.java
```
public class FibonacciTests {
    @Test
    public void testFirst10() {
        int n = 10; // Just for testing, will make it user-input later
        for (int i = 0; i < n; i++) {
            System.out.print(fib(i) + " ");
        }
    }
}
```

* test.sh
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore FibonacciTests
```
