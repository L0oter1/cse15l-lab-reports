This writeup covers the 3 command line prompts I've learned for the first week fo CSE 15L

# `cd`

The `cd` command stands for change directory. It is meant to be used with an argument to go to a new directory.

## **No Arguments**

<img width="243" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/4b826063-971b-40f6-a7f3-3acd72f70cf7">

We first started off with `pwd` which shows that our working directory is /home/. With that after we used `cd` which did not give an output. Afterwards, we check our working directory and see that there is no change. This is to be expected because we did not put in an argument for cd.


## **Directory as Argument**

<img width="268" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/7071f8ff-7f41-4d13-983c-0294f6be96bb">

Once again `pwd` shows that that we are at /home/. Afterwards, we use `cd lecture1` as lecture1 is our directory and in doing so, we change our working directory once we print out our directory once more. We now see that our working directory is at /home/lecture1.


## **File as Argument**

<img width="429" alt="image" src="https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/b5ffd9d1-a32f-4df7-83a9-8e863fd7ec3f">

When using `pwd`, we see we are at the directory of /lecture1/messages. When we use `cd en-us.txt`, we are putting in the file en-us.txt as the argument for `cd` and we get the output: *bash: cd: en-us.txt: Not a directory*. This happens because `cd` stands for change directory so when you choose a file as an argument, `cd` will let you know that it is wrong as you can't change your directory into a file. 

# `ls`


# `cat`
