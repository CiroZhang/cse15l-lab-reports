# Question 1: Bugs

We will looks that the bug in the reversed method of the ArrayExamples class

* input: {1, 2, 3, 4, 5} --> excepted output: {5, 4, 3, 2, 1}
```
@Test
public void testReversed12345() {
    int[] input = {1, 2, 3, 4, 5};
    int[] output = {5, 4, 3, 2, 1};
    assertArrayEquals(output, ArrayExamples.reversed(input));
}
```
JUnit test will fail

* input: {0, 0, 0, 0, 0} --> excepted output: {0, 0, 0, 0, 0}
```
@Test
public void testReversed00000() {
    int[] input = {0, 0, 0, 0, 0};
    int[] output = {0, 0, 0, 0, 0};
    assertArrayEquals(output, ArrayExamples.reversed(input));
}
```
JUnit test will pass

* Here we added two additional test methods
1. testReversed33333: input = {3, 3, 3, 3, 3}
2. testReversed54321: input = {5, 4, 3, 2, 1}
<br>

![Image](Junit_Error.png)

<br>

Here we see with our Junit result that testReversed12345, testReversed33333, and testReversed54321 all failed to pass the assert
AssertArrayEquals also gave us the symptom of each: 
1. testReversed12345: first index of output should be 5, but instead we got 0.
2. testReversed33333: first index of output should be 3, but instead we got 0.
3. testReversed54321: first index of output should be 1, but instead we got 0.
<br>

* The Bug our orginal code as was that it tried to assigned the reverse values of newArray to arr instead of the other way arround. And because of this bug, our output will be a array with only zeros regardless of the input
  
  
Original Code with bug
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

<br>

New Code without bug
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
<br>
Junit Passes

![Image](Junit_Pass.png)

<br>

Knowing the bug, it was a pretty easy fix. All we have to do is swap arr and newArray
1. Line 4: swap arr and newArray so we can have the reverse values of arr assigned to newArray
2. Line 6: return newArray instead of arr

<br>

# Question 2: Researching Commands

* For this question we will look at the grep command. 
* Sources: geeksforgeeks
* Link: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

1. grep -c

```
(base) cirozhang@Ciros-MBP-2 technical % grep -c "is" biomed/rr37.txt
157
(base) cirozhang@Ciros-MBP-2 technical % grep -c "scientific community" plos/*.txt
... (parts omitted) ...
plos/pmed.0020242.txt:0
plos/pmed.0020246.txt:0
plos/pmed.0020247.txt:0
plos/pmed.0020249.txt:0
plos/pmed.0020257.txt:0
plos/pmed.0020258.txt:0
plos/pmed.0020268.txt:0
plos/pmed.0020272.txt:0
plos/pmed.0020273.txt:0
plos/pmed.0020274.txt:0
plos/pmed.0020275.txt:0
plos/pmed.0020278.txt:0
plos/pmed.0020281.txt:1
```

we see here by using "-c", grep returns the number of lines in the find we search for rather than the texts inside. This could be very usefull if we are just looking for how many lines our in a specific file and we dont care about the content. 

3. grep -l

```
(base) cirozhang@Ciros-MBP-2 technical % grep -l "is" biomed/rr37.txt              
biomed/rr37.txt
(base) cirozhang@Ciros-MBP-2 technical % grep -l "scientific community"  plos/*.txt
plos/journal.pbio.0020001.txt
plos/journal.pbio.0020105.txt
plos/journal.pbio.0020161.txt
plos/journal.pbio.0020214.txt
plos/journal.pbio.0020430.txt
plos/pmed.0020035.txt
plos/pmed.0020036.txt
plos/pmed.0020281.txt
```
we see here by using "-l", grep returns the list of file names that matches our search rather than the contents inside. This could be very usefull if we are just looking for specific file names that match our search. 



5. grep -i

6. grep -h
