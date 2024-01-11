# Lab Report 1 for CSE 15L

This writeup covers the 3 command line prompts I've learned for the first week for CSE 15L and the 3 different types of arguments you can put in and their possibly unique outputs in the command line. 

# `cd`

The `cd` command stands for change directory. It is meant to be used with an argument to go to a new directory.

## **No Arguments**

<img width="243" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/4b826063-971b-40f6-a7f3-3acd72f70cf7">

We first started off with `pwd` which shows that our working directory is /home/. With that after we used `cd` which did not give an output. Afterwards, we check our working directory and see that there is no change. This is to be expected because we did not put in an argument for cd.

<img width="378" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/fe449035-dbbe-4b7d-ac6a-de214195a129">

Another use of `cd` is to go directory back to the home directory. As seen in this screenshot, when I use `pwd`, we are at /home/lecture1 but when we use `cd` again, we see that we are now in the /home/ directory. 

## **Directory as Argument**

<img width="268" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/7071f8ff-7f41-4d13-983c-0294f6be96bb">

Once again `pwd` shows that that we are at /home/. Afterwards, we use `cd lecture1` as lecture1 is our directory and in doing so, we change our working directory once we print out our directory once more. We now see that our working directory is at /home/lecture1.


## **File as Argument**

<img width="429" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/b5ffd9d1-a32f-4df7-83a9-8e863fd7ec3f">

When using `pwd`, we see we are at the directory of /lecture1/messages. When we use `cd en-us.txt`, we are putting in the file en-us.txt as the argument for `cd` and we get the output: *bash: cd: en-us.txt: Not a directory*. This happens because `cd` stands for change directory so when you choose a file as an argument, `cd` will let you know that it is wrong as you can't change your directory into a file. 

# `ls`

The `ls` command stands for list. It is meant to be used without an argument to give the user a list of possible files and directories from the working directory you are in right now. 

## **No Arguments**

<img width="379" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/982304d4-34cb-4c07-91ff-4cce33548255">

When we give no arguments, we see that ls lists the possible files and directories that exists in our working directory. As seen our wd (working directory) is /home/lecture1 and so `ls` without arguments listed all the possible files and directories that exists, that being Hello.class, Hello.java, messages, and README. 

Note: Apparently it seems that directories are bolded and blue when I use ls. 


## **Directory as Argument**

<img width="373" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/f1f07cb2-918f-404a-b819-d18b3c5e8411">

We see here with `pwd` that we are at /home/lecture1. When we use `ls (directory)`, ls lists the possible directories and files as if you were in that working directory so when we used `ls messages`, it listed all the files inside messages. However once we use `pwd`, we see that did not change our working direcotry and only showed us what was inside the directory we chose to make our argument. 

## **File as Argument**

<img width="379" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/d7e9e734-22ea-47c1-bfb3-cc76606b2fde">

We see here that we are still in the /home/lecture1 directory and have the option to use ls to see what is inside this directory. Afterwards we see there are possible files and not directories. When I used the Hello.java file as the argument for ls, the output is just the file itself. It also did not change my working directory. 

# `cat`

The `cat` command is short for concatination and is made to print out the text from a file. 

## **No Arguments**

<img width="199" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/05c7fcff-7cb9-45b3-b991-cac2584d2645">

We are in the home directory. When we use `cat`, the terminal becomes really weird where you aren't being prompted or allowed to put in any proper commands and it just becomes blank and goes on and on forever until you force exit it out. It is very strange. 

## **Directory as Argument**

<img width="376" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/bac15e66-e03d-41ce-80db-cd10bddc614c">

When we use cat with a directory as an argument, we see it throws us an output *cat: messages: Is a directory*. It seems cat can't do anything with a directory so they just tell you you chose a directory.

## **File as Argument**

<img width="375" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/7c19c6c5-6241-42dd-af6b-20e8ccaa8424">

As you can see our pwd is in /home/lecture1 so when we use `cat` with an argument that is a file, it will print out everything inside the file that is text. However there are more uses for cat because cat stands for concatonate so it should be able to combine things right?

<img width="728" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/878394cb-b3c9-4a88-a838-398f296ad248">

As you can see here you can use multiple inputs such as in this example where I use the file of README and Hello.java, it will print out everything from those files in order. 

<img width="726" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/9905b98d-0305-4364-bb02-05eac477c60e">

Lastly just for fun, I chose to add a file that is a .class file which is unreadable for humans. The cat command printed some really weird stuff that's still in english but makes zero sense. 

