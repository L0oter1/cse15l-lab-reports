# Lab Report 4 for CSE 15L

# Reproducing Steps 4-9 for Use of Vim

# Step 4
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/c5770fc2-66e5-4ef7-b8f4-d2ad235d6bfd)

## Keys Pressed

ssh`<space>` jthi@ieng6-201.ucsd.edu `<enter>`

## Explanation

Since I started a new terminal, there was no stored previous command so I had to literally hand type everything to log into the ssh of ucsd.
I had to log into 201 becausethe default server you log into doesn't have jdk installed so my java commands wouldn't work.
After I enter, I will automatically log in because I have a key stored on my computer so I don't have to enter password.


# Step 5
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/8ac8bf0c-8882-4a89-b517-8592773b9c9d)

## Keys Pressed

git `<space>` clone `<space>` `<ctrl>` v

## Explanation

I had to clone the respository so I typed in `git clone`. Afterwards, I already had the ssh key for the forked repository from github so I only
had to use `control v` to paste the copied code from clipboard to the directory on ucsd servers.


# Step 6
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/1bede1f6-c443-4dcd-be22-91e457553e80)

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/edd13784-4470-4e84-a749-6c2aac785767)

## Keys Pressed
cd `<space>` l `<tab>` `<enter>`

bash `<space>` t `<tab>` `<enter>`

## Explanation
I first cd into the directory of the downloaded github clone and go into the directory of lab7/ but I only had to type l since there
was only one directory that started with l and then I just pressed `<tab>` in order to autofill into the directory.

After I got into the directory, I typed in bash and then after a space, I typed t and then `<tab>` since there was only one filed that started with
t which was the test.sh file and then I only had to press `<enter>` because it autofilled for me.


# Step 7
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/649fdccb-a60e-487e-9c3d-0367dff7648e)

## Keys Pressed
vim `<space>` L `<tab>` . `<tab>` `<enter>`

:44 `<enter>` e r 2 :wq

## Explanation
First i had to open the ListExamples.java file with vim which is why I typed vim. After a space, I used a capital L since vim tab seems case sensitive.
That allowed it to autofill to ListExamples only because there was also a ListExamplesTests.java file so after I typed a "." I pressed tab once more 
which selected the correct file and pressed enter

Once in, I did what I did in my lab and used ":44" to go to line 44 immediately. After I used "e" to go to the end of the first word of the line. With that
I pressed "r2" to replace the last character of "1" with "2" without even needing to go into insert word. I then pressed ":wq" to write the correction and then
quit.


# Step 8
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/0ec8b7f2-feee-4fc1-91c6-b63275b72f6e)

## Keys Pressed
`<up>` `<up>` `<enter>`

## Explanation
After I exited out of vim, all I had to do was use the `up` array a couple of times because I had the bash script command saved. First up arrow went back to 
vim command and second up arrow went back to the bash script command which I then pressed enter to run the script again.


# Step 9
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/1ceff8b9-aeb9-4e4e-9446-d38cdda4f83a)

## Keys Pressed
git `<space>` add `<space>` L `<tab>` . `<tab>` `<enter>`

git `<space>` commit `<enter>`

i I added 2 at the end lol `<esc>` :wq

git `<space>` push

## Explanation
I first would git add the file I changed to github with the first command listed. I can once again autofill in the ListExamples.java file.

Afterwards, I will commit which prompts me to write a commit update using vim. 

In vim, I would press "i" to get into insert made. Then type my sentence which was "I added 2 at the end lol" then press `<esc>` to get out of insert mode. Then 
I would use ":wq" to save and exit out of vim.

Lastly I would use git push. I wouldn't have to type in a username or password for github because I already added the key to my school account for my github so when I git cloned using ssh, it would automatically push without the need of typing in a username and password for github.


