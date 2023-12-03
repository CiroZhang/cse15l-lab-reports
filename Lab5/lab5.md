# Original Post by Student

Title: Issue with Java Program Output

Hi everyone,

I'm having a strange issue with my Java program. I'm supposed to print the Fibonacci sequence up to a given number, but the output is not what I expected. Here's a screenshot of the output:




```
public class Fibonacci {
    public static void main(String[] args) {
        int n = 10; // Just for testing, will make it user-input later
        for (int i = 0; i < n; i++) {
            System.out.print(fib(i) + " ");
        }
    }

    public static int fib(int n) {
        if (n <= 1)
            return n;
        else
            return fib(n-1) + fib(n-2);
    }
}
```
