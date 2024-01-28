# Lab Report 2 for CSE 15L

## My Code
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/b010dd9e-fd5a-4347-aa50-d779cfa6292f)

## Screenshot 1
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/faade59d-e50c-4d27-b8b3-78f971646ce2)

## Screenshot 1 Explanation
`methods called` <br>
The method that called in my code is the main and handleRequest methods.

`arguments for methods` <br>
`main` method argument: **String[] args** : It is used to determine which port number is used to run the website locally on my computer. <br>
`handleRequest` argument: **url** : It takes in the url for the website and the subsequent code is used to determine what to do based on the url provided <br>

`relevant fields` <br>
In my handleRequest method, there is an arrayList field called `list` that stores the String that is formated according to the lab instructions
Parameters field which stores the query of the url using an `=` to split each part into a seperate index. Its second index stores the name of the user 
Paramteres2 field stores the 1st index of parameters split based on `&` to store the message said to user 
`changing values` <br>
Values did get changed. Because I changed the url, the url used as the argument for the handleRequest method is changed and thus the method runs a program accordingly
Based on the url, query is updated to: **?s=Hello&user=jpolitz**
This then updates the `parameteres` variable into **{?s, Hello&user, jpolitz}** 
From there, `parameters2` is updated into **{Hello, user}**
Then we append the list to store the string: **`jpolitz` + ": " + `Hello` + \n** with jpolitz coming from `parameters[2]` and Hello coming from `parameteres2[0]`
Now our list variable has a new index with a new string.
We also have an `answer` variable which is just a temporary string created to print out all the strings inside the list variable.




## Screenshot 2
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/3a983366-c079-41e7-b1bc-75e6ec391b63)
<br>
<br>
## Screenshot 2 Explanation 
`methods called` <br>
The method that called in my code is the handleRequest method.

`arguments for methods` <br>
main does not run when I change my url because my server is still up from starting it previously. <br>
handleRequest argument: **url** : It takes in the url for the website and the subsequent code is used to determine what to do based on the url provided <br>

`relevant fields` <br>
In my handleRequest method, there is an arrayList field called list that stores the String that is formated according to the lab instructions
Parameters field which stores the query of the url using an `=` to split each part into a seperate index. Its second index stores the name of the user
Paramteres2 field stores the 1st index of parameters split based on `&` to store the message said to user

`changing values` <br>
Values did get changed. Because I changed the url, the url used as the argument for the handleRequest method is changed and thus the method runs a program accordingly
Based on the url, query is updated to: **?s=How are you&user=yash**
This then updates the `parameteres` variable into **{?s, How are you&user, yash}** 
From there, `parameters2` is updated into **{How are you, user}**
Then we append the list to store the string: **`yash` + ": " + `How are you` + \n** with jpolitz coming from `parameters[2]` and Hello coming from `parameteres2[0]`
Now our list variable has a new index with a new string.
We also have an `answer` variable which is just a temporary string created to print out all the strings inside the list variable.


## Private Key
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/3d7ab1ab-5b3f-4fab-90d0-a041f9056f85)

**Absolute Path :**  C:\Users\jeffr/.ssh/id_rsa

## Public Key
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/f09acf49-83ac-4bba-ad66-0b80ffc3577e)

**Absolute Path :** C:\Users\jeffr/.ssh/id_rsa.pub

## No Password Request
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/e76fe2f0-e9eb-42fa-a6d9-af2420f6677c)


## What I Learned 
`mkdir` I learned that mkdir creates a new directory which you can title files that start with a period such as .ssh.

`scp` I learned that scp copies securely from a source online to your local computer.

`ssh` Yhis is where you can create and store Keys on your computer so you don't have to type in a password a second time when you try to log into a ssh. There are two types of keys, pubic and private keys.

`Server Hosting` I learned that with java and probably other programming languages, you're able to host a website locally on your computer for you computer to access as well as host on a server for any computer with the link to the website to be able to access it. 
With this website, you can also use code to program different methods that run based on the url that is inputted into the website. 

`port` I learned that computer has different ports where the beginning ones do specific things but higher numbered ports are open and can be used to host servers or do other things.











