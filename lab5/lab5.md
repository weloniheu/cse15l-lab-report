## Part 1 – Debugging Scenario<br>
Design a debugging scenario, and write your report as a conversation on EdStem. It should have:<br>

The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don’t actually make the post! Just write the content that would go in such a post)<br>
A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)<br>
Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.<br>

### Edstem 

**Student:** 

Hello, I've been trying to work on some code to work on my bash calls so I wrote some simple code on with the Fibonacci seqeunce however I can't even get my code to work, I'm getting this crazy bug where it just prints a bunch of stuff over and over again that doesn't even look like high values of fibonacci. Luckily I was able to ctrl c before my terminal got too crowded. The bug must be in the while loop but I don't understand, it shouldn't go on forever because I know I'm incrementing i. <br>

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/653ef609-93e6-4011-8d68-3a19c5162443)

**TA:** 

I think I have an idea of what you issue may be. I know you confident are your incrementation of I in you code, but have you actually tested whether or not it is?<br><br>

**Student:** 

Nothing Changed! But it's odd that it's the same result as the previous one, could I have broken something else now?

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/f3c6c2d6-25b0-4a78-81f7-e9b7de25199b)

**TA:** 

Hmm that's odd, did you recompile the code after you made changes to it with ```javac class.java```?<br><br>

**Student:** 

Oh my goodness that's embarrasing, but still why doesn't i change at all? I'm certain I'm incrementing it. It it not being recognized by the while loop for some reason.

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/e0b5970f-95d2-439a-9c61-e62aba6dd319)

**TA:** 

Maybe go where you incrementing it over one to see why this could be the case.<br><br>


**Student:** 

Hmmm I realised I had my incremetation of I outside of the loop , but it still didn't change anything after I did it.

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/c8930979-0156-44e1-834d-5e0cb1a1eea7)

**TA:** 

This one is a little harder to explain why it's not working, perhaps try a more normal approach like ```a = b + c``` <br><br>

**Student:** 

Hmm interesting symtop I wonder why it didn't increment even though i++ add's one, so it i was 0 and it added 1 setting it to i wouldn't that work I'll have to look up why that is later. But it seems to work when I do this. . <br>

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/fe512cfc-48bf-4d68-9502-f18a4aaccd96) <br><br>

**TA:** 

Nice! And yeah always explore and try new things. And Hey it happens to the best of us sometimes.
<br><br>
**Student:** 

Okay I think I have it figure out now. So not only was I not incrementing it in the while loop the syntax that I choose wouldn't even have done anything Cool lets get to the bash stuff!

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/f246668d-ec45-4e93-b279-3d8381ebcf93)

**TA:** 

Well done! And it happens to the best of us. <br> <br>

**Student:** 

Hmm that's odd

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/a999976b-6f70-411e-8373-5aa80cd0a3bc)

**TA:** 

Recall when trying to clone something from git hub, you need to add git clone rather than just use command clone cause it wouldn't recognize it either.
<br><br>
**Student:** 

Ah right I need to write ```bash fib.sh```. But weird I it won't count again? I would think that $0 looks at the first argument and not the command but it seemed to work. What happened? (ignore my mistake)

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/dd436b57-51b4-4345-971c-b7763d61f1da)
![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/8fbe8888-65e5-4a78-83d9-70f760117e85)

**TA:** 

You are right and wrong. It's more accurate to refer to everything as a command line argument, so fib.sh is actually the first where what every you put after as the second, so on and so forth. Fun fact if you changed it to $5, it could still work but you'd need to make 6 arugments instead.
<br><br>
**Student:** 

Ahhh I see thank you for your time and patients. I was really struggling there and you really saved me and I learned a little more about how the command line works that I wasn't quite crystal clear on!


### At the end, all the information needed about the setup including:
 - The file & directory structure

  ![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/b3a36f6e-7b6e-4ed8-80dd-75a06c2600f9)<br>
  
 - The contents of each file before fixing the bug

   #### FibCalc.java
  ```
public class FibCalc {
    public static void main(String[] args) {
        int num = Integer.parseInt(args[0]);
        int first = 0, second = 1;
        System.out.print("Fibonacci sequence: ");
        int i = 0;
        while (num > i){
            System.out.print(first + ", ");
            int next = first + second;
            first = second;
            second = next;  
        }
        i = i + 1;
    }
}
  ```

  #### Fib.sh
  ```
  java FibCalc $0
  ```
  <br><br>
 - The full command line (or lines) you ran to trigger the bug

```
java FibCalc 8
```
to trigger the infinite loops

```
bash Fib.sh
```
to trigger the incorrect bash command
<br><br>

 - A description of what to edit to fix the bug

   In order to fix the bugs first that was needed was removing the infinite loop by properly identifiying what caused it. By deleting the faulty incremetation syntax ```i = i++``` and replacing it with ```i = i + 1``` into the while loop we were able to properly bring the loop to an end.
   
   For the bash file, the bug was in both how the command was called in the terminal, so an argument needed to be added for it work properly, at least as the code was written, to make it so that ```bash Fib.sh``` the chosen nth number would have to be hard coded into FibCalc.java. The other bug that arose was the .sh file feeding the first arguement, $0, rather than the second, $1, so all that needed to be changed was ```java CalcFib #0``` to ```java CalcFib #1```


<br><br><br>


## Part 2 – Reflection

I really liked learning about Vim. It seems like such a impressive tool that is able to do many different things, specifically without having to use a track pad or mouse which I've been told drastically increases the speed of the work you do which, based on my personal experiences am inclined to agree with. Although I'm still new to things in it I hope the skills I've learned from in lab/class and from friends will be of help in the future. I'm still fairly unclear on some of the things but I'm sure if I dedicate a decent amount of time, consulting the internet, friends and perhaps even chatGPT I'll get quite good at it!


