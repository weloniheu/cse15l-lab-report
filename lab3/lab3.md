### The Lab Report 3

#### Part 1


#### - A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

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

#### - An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

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

#### - The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)



#### - The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

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

#### "reverseInPlace" Method:

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

#### "reverseInPlace" Method Fixed:

    ```
    Bug Fixes:
      1:
      - create a temporary value to hold the arr[length-1-i]
      - Sets arr[length-1-i] to arr[i]
      - arr[i] the stored value of arr[length-1-i] in temp 
      Maintain the discription of InPlace and flips the values
      2:
      - the for loop is changed from going for i < length to i < length/2
      This ensures that values aren't look at more than once which would have resulted in the list being flipped back to the original orientation after passing the half way point which is not what we want.
    ```

#### "reversed" Method:

    ``` 
    Bug: 
      1. Sets the value of arr[] to the values of newArray[] which is an empty array
      2. Returns the original array rather than the new array ie returns arr;
    
    Symptoms: 
    [1, 2, 3]
    for i = 0
    it sets the value of A[0] to length-0-1 of the newArray or newArray[2], which are the values 0
    The A[0] is set to newArray[2]
    [0, 2, 3]
    
    then for i = 1
    it sets the value of A[1] to length-1-1 of the newArray or newArray[1], which are the values 0
    The A[0] is set to newArray[2]
    [0, 0, 3]
    
    etc
    
    Doesn't reverse but rather deletes the original array which in turn returns an empty array.
    
    ```

#### "reversed" Method Fixed:

    ```
    Bugs Fixes:
      1:
      - set newArray[i] to arr[arr.length-1-i]
      Stores the values of arr[] in the reversed order in newArray[]
      2:
      - return newArray;
      Returns the newly created reversed copy of arr
    ```



