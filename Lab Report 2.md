# Lab Report 2 for CSE 15L

## My Code
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/b010dd9e-fd5a-4347-aa50-d779cfa6292f)

## Screenshot 1
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/faade59d-e50c-4d27-b8b3-78f971646ce2)

## Screenshot 1 Explanation
`methods called :`
The method that called in my code is the main and handleRequest methods.

`arguments for methods :`
main method argument: **String[] args** : It is used to determine which port number is used to run the website locally on my computer.
handleRequest argument: **url** : It takes in the url for the website and the subsequent code is used to determine what to do based on the url provided

`relevant fields :`
In my handleRequest method, there is an arrayList field called list that stores the String that is formated according to the lab instructions
Parameters field which stores the query of the url using an `=` to split each part into a seperate index. Its second index stores the name of the user
Paramteres2 field stores the 1st index of parameters split based on `&` to store the message said to user

`changing values :`
Values did get changed. Because I changed the url, the url used as the argument for the handleRequest method is changed and thus the method runs a program accordingly
Based on the url, query is updated to: **?s=Hello&user=jpolitz**
This then updates the `parameteres` variable into **{?s, Hello&user, jpolitz}** 
From there, `parameters2` is updated into **{Hello, user}**
Then we append the list to store the string: **`jpolitz` + ": " + `Hello` + \n** with jpolitz coming from `parameters[2]` and Hello coming from `parameteres2[0]`
Now our list variable has a new index with a new string.
We also have an `answer` variable which is just a temporary string created to print out all the strings inside the list variable.

## Screenshot 2
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/3a983366-c079-41e7-b1bc-75e6ec391b63)

## Screenshot 2 Explanation 
`methods called :`
The method that called in my code is the handleRequest method.

`arguments for methods :`
main does not run when I change my url because my server is still up from starting it previously.
handleRequest argument: **url** : It takes in the url for the website and the subsequent code is used to determine what to do based on the url provided

`relevant fields :`
In my handleRequest method, there is an arrayList field called list that stores the String that is formated according to the lab instructions
Parameters field which stores the query of the url using an `=` to split each part into a seperate index. Its second index stores the name of the user
Paramteres2 field stores the 1st index of parameters split based on `&` to store the message said to user

`changing values :`
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
`mkdir` creates a new directory which you can title files that start with a period.

`scp` copies securely from a source online












