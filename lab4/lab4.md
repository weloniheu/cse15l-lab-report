### The Lab Report 4

#### Procedure

##### Log into ieng6

To do this I typed 
```ssh cs15lfa23ef@ieng6.ucsd.edu<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/b7fed2ec-b571-4d0e-934a-1213dfc43325)


##### Clone your fork of the repository from your Github account (using the SSH URL)

To do this I clicked the copy button in github for the ssh link.

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/486a988e-9545-4020-a028-3ed45d0ab12a)


I think pasted the ssh link into the with git clone.
```git clone git@github.com:weloniheu/lab7.git<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/db4ab062-bcab-425b-be1e-8783eb70ada3)


##### Run the tests, demonstrating that they fail


To do this ls to make sure I had knew which was the bash file for lab7 and then ran with it with bash.
```ls<enter>```
```bash test.sh<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/c1cef9d5-c1a0-4956-9d42-bc98a6ff9b03)



##### Edit the code file to fix the failing test


To do this I first needed to enter the code which can be done with the program **vim** that we learned in class. I also remembered that I could use tab to finish the rest of existing files to quicken the process.
```vim Lis<tab>.j<tab><enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/db54b8aa-1a2d-49c3-85b8-9a7827c7aa8c)



To edit the text, while still in normal mode I pressed shift G to move to the end of the file and then k to move up towards the line that needed to be checked.
```<shiftG><k><k><k><k><k><k><l><l><l><l><l><l><l><l><l><l><l>```
or
```<movetoend><up><up><up><up><up><up><right><right><right><right><right><right><right><right><right><right><right>```

once the cursor was where I wanted i pressed r and then changed the 1 in index1 to 2 so that it becomes index2.

```<r><enter><2><esc>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/b87c00cb-0ed1-4076-ad92-f3ff3e99a0ec)



then I exited with the save and quit command

```:wq<enter>```

##### Run the tests, demonstrating that they now succeed


As I already ran the bash test.sh earlier I pressed up arrow to get there, however as I entered vim a number of times the numbers represent a higher amount if you look at the number$:. Also interesting enough vim ListExamples.java is considered different commands from vim ListExamples.java<space> for the purposes of the shells list of previous commands, so I needed to press up twice to get back to my test.sh command from earlier. 

```<up_arrow><up_arrow><enter>```

Ie vim ListExamples.java<space> -> vim ListExamples.java -> bash test.sh

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/b329778e-b986-4516-817e-23e60f690637)



##### Commit and push the resulting change to your Github account (you can pick any commit message!)


To do this I first added the file with the git add command I then checked with git status to make sure it was in 

```git add Lis<tab><enter>```
```git status<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/35936e21-79e4-4700-9ecb-885ec111384b)



Once I was certain it was added I did the commit modified command with git commit -m with "Bug Fixed". Then checked with git status again.

```git commit -m "Bug Fixed"<enter>```
```git status<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/cbb80215-7e6d-4b1a-b5a8-c907aed1d07b)



Finally sure it used the push command to add it to the github.

```git push<enter>```

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/8367e257-dbce-4a5b-9eb8-a9fce568dcf0)

![image](https://github.com/weloniheu/cse15l-lab-report/assets/115903567/487a75e2-0a16-4169-8535-e985072737d8)

