# Lab Report 5 Putting It All Together (Week 9)

## Part 1 – Debugging Scenario

## 1. Original Post with Screenshot

**Bug**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/24124b5e-d7be-4e1f-a063-43c60089f53d)

**Symptom**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/56b2ce44-61eb-41d7-b044-55bb10088a16)

### Problem: 

I'm tasked with printing out the compiler error message into the respective file titled error-messages.txt of each submission directory if there is a compilation error. I see that the error is printed into the terminal when there is an error but I'm not sure why the compiler error message can't be put into a text file with `> error-messages.txt`.
I'm not sure if there is a specific syntax that can get me the error message returned from the last call of a command.

### Guess of Bug:

I'm guessing there might be special syntax such as another `?(character)` that allows me to gain access to the last returned error message of a method instead of using `>`. It might also be because I compile a file again in order to get the output of compiler error but I'm pretty sure I'm allowed to do that. I just don't know why the specific line of code `javac Sorter.java > error-messages.txt` doesn't work.



## 2. TA Response

I can see you're almost there. Your thought process of rerunning the compile command to get the error message is correct as you are allowed to run compile multiple times in the same bash script. It would be very helpful if you review week 6's lab about autograding and look up the difference between standard output and standard error, and how you can redirect those two messages into a text file. Although they are both outputs, bash still registers them differently and thus you might need to do something different for each.



## 3. Screenshot of Following Advice

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/f7b225c5-82f3-463a-8a03-b459714c36ad)

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/61a1f004-2448-434e-887b-ab6e7afefa57)


### Description of Bug:

Thank you! I've searched it up by asking chatgpt what the difference between standard output and standard error is in bash. It told me that in bash, there are different syntax for redirecting standard error and standard output and so for error, I had to use `2>` instead of `>`. Now everything works correctly! Thanks!


## 4. All Info Needed

### The file & directory structure needed
- skill_demo_3_private/
  - submissions/
    - studentB/
      - error-messages.txt
      - result.txt    
      - Sorter.java 
  - grade.sh

### The contents of each file before fixing the bug
**error-messages.txt**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/b3508619-c22a-49b2-9f36-e9a44e5743cb)

**result.txt**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/282c3236-3035-4afb-8a35-c946daba13fc)

**Sorter.java**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/7a94ff6b-afe5-431e-80b2-b8c5e39633d5)

**grade.sh**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/ad1422b8-ac2d-459c-9987-b5ae8e67a7c7)


### The full command line (or lines) you ran to trigger the bug

1. `cd skill_demo3_private`
2. `bash grade.sh`

### A description of what to edit to fix the bug

The edit that fixed the bug was changing `>` to `2>` because what we were asked to print out was standard error from the compiler command and not the standard output from the program. Because of this, I specifically changed `javac Sorter.java > error-messages.txt` into `javac Sorter.java 2> error-messages.txt`. This way when the exit code from compiler is not 0, aka there is an error, the file will compile again knowing there is an error and use `2>` to redirect the error into the appropriate text file inside that submission's directory. 


## Part 2 - Reflection

Something interesting I learned was about the programming process when you work at a company. I always thought you were expected and given permission to download the code from your company and edit it on your local text editor but apparently you're not allowed to because that is a big security risk. So instead what they do is they have you log in through ssh and edit code through the terminal using vim or other terminal text editors. I just found that so interesting because I've never used vim before and the idea that you could edit code in the terminal without a text editor just amazes me. 

The applications of vim are really cool especially when you have so many unique commands that can do different things to increase your efficiency such as `:(line number)` to go to a specific line or `r(character)` to replace a character your cursor is on without having to enter editor mode. 

Another cool thing I learned was jdb. It was crazy how you can add stops to the program to see where the bug is and how you can print out the all the local variables. What was cool was how it was like writing code where at a certain stop, you could print out not just variables but also functinos of variables such as printing out hash.lenght by typing `print hash.length`.

All in all, a summary of what I learned was how to code in the terminal. Usually you use VSCode, JUnit, and print statements to look and code for bugs but who knew you could also and are expected to use Vim, and JDB to do the same thing but it's all in the terminal since you need to use ssh. And to top it all off, I've always wanted to learn how to use github and I finally got to learn what it is and how to use it, so now I feel like an actual programmer now. 
