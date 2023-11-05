### The Lab Report 3

#### Part 1


- A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

    ```
    import static org.junit.Assert.*;
    import org.junit.*;
    
    public class ArrayTests {
    	@Test 
    	public void testReverseInPlace() {
        int[] input1 = { 3, 4, 5, 6 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 6, 5, 4, 3 }, input1);
    	}
    
      @Test
      public void testReversed() {
        int[] input1 = { 3, 4, 5, 6 };
        assertArrayEquals(new int[]{ 6, 5, 4, 3 }, ArrayExamples.reversed(input1));
      }
    }
  
    ```
    
- An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

    ```
    import static org.junit.Assert.*;
    import org.junit.*;
  
      public class ArrayTests {
      	@Test 
      	public void testReverseInPlace() {
          int[] input1 = { 1 };
          ArrayExamples.reverseInPlace(input1);
          assertArrayEquals(new int[]{ 1 }, input1);
      	}
    
      @Test
      public void testReversed() {
        int[] input1 = {};
        assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
      }
    }
    ```

 - The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)



 - The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

    ```
    ///Broke Code
    public class ArrayExamples {

      // Changes the input array to be in reversed order
      static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = arr[arr.length - i - 1];
        }
      }
      // Returns a *new* array with all the elements of the input array in reversed
      // order
      static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
        }
        return arr;
      }
    }
    ```
  
    ```
    //fixed Code
    public class ArrayExamples {
  
      // Changes the input array to be in reversed order
      static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length/2; i += 1) {
          int temp = arr[arr.length - i - 1];
          arr[arr.length - i - 1] = arr[i];
          arr[i] = temp;
        }
      }
      // Returns a *new* array with all the elements of the input array in reversed
      // order
      static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
          newArray[i] = arr[arr.length - i - 1];
        }
        return newArray;
      }
    }

    ```

- Briefly describe why the fix addresses the issue.

##### "reverseInPlace" Method:

    ``` 
    Bug: 
    1. Doesn't "move" the values in the front to the back
    2. Passes over already visited values
    
    Symptoms: 
    [1, 2, 3]
    for i = 0
    it flips the item in A[0] and length-0-1 or A[2], which are the values 1 and 3 respectively 
    The A[0] is set to A[2]
    [3, 2, 3]
    
    then for i = 1
    it flips the item in A[1] and length-1-1 or A[1], which is the value 2
    A[1] remains the same as it's set to itself
    [3, 2, 3]
    etc.
    
    Doesn't reverse but rather Mirrors the back of the array to the front
  
    ```

##### "reverseInPlace" Method Fixed:

    ```
    Bug Fixes:
      1:
      - create a temporary value to hold the arr[length-1-i]
      - Sets arr[length-1-i] to arr[i]
      - arr[i] the stored value of arr[length-1-i] in temp 
      Maintain the discription of InPlace and flips the values
      2:
      - the for loop is changed from going for i < length to i < length/2
      This ensures that values aren't look at more than once which would have resulted in the list being 
      flipped back to the original orientation after passing the half way point which is not what we want.
    ```

##### "reversed" Method:

    ``` 
    Bug: 
      1. Sets the value of arr[] to the values of newArray[] which is an empty array
      2. Returns the original array rather than the new array ie returns arr;
    
    Symptoms: 
    [1, 2, 3]
    for i = 0
    it sets the value of A[0] to A.length-0-1 of the newArray or newArray[2], which are the values 0
    The A[0] is set to newArray[2]
    [0, 2, 3]
    
    then for i = 1
    it sets the value of A[1] to A.length-1-1 of the newArray or newArray[1], which are the values 0
    The A[0] is set to newArray[2]n 
    [0, 0, 3]
    
    etc
    
    Doesn't reverse but rather deletes the original array which in turn returns an empty array.
    
    ```

##### "reversed" Method Fixed:

    ```
    Bugs Fixes:
      1:
      - set newArray[i] to arr[arr.length-1-i]
      Stores the values of arr[] in the reversed order in newArray[]
      2:
      - return newArray;
      Returns the newly created reversed copy of arr
    ```



#### Part 2


I asked ChatGPT  "Can you give me 4 grep commands in bash outside of the base grep command"

ChatGPT replied 

"Certainly! Here are four grep commands in Bash that utilize some of the extended features and options available outside of the basic grep command:"

1. Using 'egrep' (Extended 'grep') to search for multiple patterns:

```egrep "pattern1|pattern2" filename.txt``` in bash

This command uses 'egrep' to seach for lines containing either "pattern1" or "pattern2" in the file 'filename.txt'. The '|' (pipe) character functions as a logical OR. 

2. Using grep with the -B and -A options (Before and After Context Lines):

```grep -B 2 -A 2 "search_term" filename.txt``` in bash

will search for "search_term" in the file 'filename.txt' and show two lines before and two lines after each match, providing a more comprehensive view of the context in which the search term appears in the file. You can adjust the number of context lines as needed by changing the values for '-B' and '-A'.

3. Using 'grep' with word boundaries for exact word matching 

```grep -w "exact_word" filename.txt``` in bash

This command utilizes the '-w' option to match the word "exact_word" exactly, ignoring partial matches or substrings in the file 'filename.txt'.

4. Using grep with the context option to display surrounding lines:

```grep -C 2 "search_term" filename.txt``` in bash

This command uses the '-C' option to display two lines of context (one line before and one line after) for each occurrence of "search_term" in the file 'filename.txt'.

These 'grep' commands demonstrate some advanced features and options that can be used to enhance your text pattern searching and matching capabilities. You can adapt these commands to suit your specific search requirements


I made note of the slight difference between egrep, as the one that was given to me, and grep so I asked ChatGPT "what is the difference between egrep and grep"

Which it replied giving a fairly long explination but the summary was.

"the main difference is that 'egrep' supports Extended Regular Expressions, making it easier to write and read regular expressions that include special characters. 'grep', on the other hand, uses Basic Regular Expressions by default, so you would need to escape these special characters if you want to use them in your regular expressions. You can also enable Extended Regular Expressions in 'grep' by using the '-E' option, like 'grep -E "pattern" filename.txt', which would make it function similarly to 'egrep'."




Example 1: egrep


Being able to look for a line where it potentially has a pattern "or" another pattern or maybe even a pattern "and" another pattern. With a lot of customation for the expression made can allow for expanded searches or very particular searches with some variance.

Example 2: grep -B and -A

Being able to look at context before or after could be useful when you want to know a little more about the line that grep pulls up.

Example 3: grep -w

Finding the exact word you are looking for is another way of narrowing down the search. If you have a lot of file to look through and you want to look up a relatively short word this ensures it doesn't find overlaps that aren't that word specifically ie. bar could potentially be a part of other words, but with -w you'd only get bar.

Example 4: grep -C

Like -B and -A but it's a short hand to incompass both so it's just faster to type but provides the same benefits.








