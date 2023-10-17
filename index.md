<p align="center">

## **The Lab Report**

### **The Cd Command**

<p aligh="left">

#### **Cd with no arugment**

- "cd" did nothing and only created a new line waiting for another command

  ![Image](No_Argument_cd.png)

- if you do "cd" while in working directory other than /home it returns you to know for edstem terminal

  ![Image](No_Argument_cd_noHome.png)

#### **Cd with a Directory**

- "cd" entered the directory that I wrote after it
  
  ![Image](Directory_cd.png)

#### **Cd with a File**

- "cd" command failed as this is a file and not a directory

##### **NOTE**

- all of the commands when attempting to access the directory "messages" while not in "lecture1" all had slightly different but ultimately it wasn't something can could be viewed from [user@sahara~]$ (see left) if I wanted it to work I would need to cd lecture1, which would bring me to a [user@sahara ~lecture1]$ (see right) where I could then enter messages, using any of the commands tho cat also

![Image](Directory_All_messages_lecture1Closed.png) ![Image](Directory_All_messages_lecture1Open.png)

  
  ![Image](File_cd.png)

##### **NOTE**

Being that there are no file in the base Workspace I needed to cd into Lecture1 to access the files to proper attempts the commands else it will say "no such directory or file" similar when we attempt to use commands on a directory that it couldn't access. This holds true for all the commands used in this lab

![Images](File_All_Error.png)


<p align="center">

### **The ls Command**

<p aligh="left">

#### **ls with no arguments**

- "ls" wrote in the terminal the only item in the workplace "lecture1" then created a new line waiting for another command

![Image](No_Argument_ls.png)

#### **ls with a Directory**

- "ls" wrote down the name of files and directorys with in the choosen directory but only the names.
  
![Image](Directory_ls_lecture1.png) 

#### **ls with a File**

- "ls" copied it's own name as it's the only item in that list
  
![Image](File_ls.png)

<p align="center">

### **The cat Command**

<p aligh="left">

#### **cat with no arguments**

- "cat" was a little more interesting while it didn't write anything to the terminal and did create a new line it didn't have [user@sahara~]$. Instead anything that I wrote afterwards would be repeated as though I had called the cat command on those statements. This included just pressing enter skipping two lines instead of one. In order to leave I learned via google that ctrl-d would allow me to back track to once again show [user@sahara~]$

![Image](No_Argument_cat.png)

#### **cat with a Directory**

- "cat" wrote in the terminal "lecture1: is a directory" which just means you can't copy the context of a directory. This makes sense cause if it was able to cat, it would have to also look with in a directory to find files in it print out, I image there are too many edge cases to make it worth it. Although there maybe another command we have haven't encountered yet with that functionality.

![Image](Directory_cat_lecture1.png)

#### **cat with a File**


- "cat" copied the contents of the file

![Image](File_cat.png)





