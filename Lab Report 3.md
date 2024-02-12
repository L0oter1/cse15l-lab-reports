# Lab Report 3 for CSE 15L

# Part 1 Bugs 🐛

## Failure Inducing Test

```
@Test 
public void testReverseInPlace() {
    int[] input2 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 3, 2, 1}, input2);
}
```


## Non Failure Inducing Test
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

## Symptom of Problem 
![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/cb11a332-e6a4-4801-827e-550d3a9ef224)


## The Bug

**Before**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/a7d866b1-797e-406e-9739-0ac136058657)


**After**

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/c05a85c2-341d-4ed6-a5dc-5ce6411f1fad)


**Explanation**
The issue with the original code was that there wasn't a way for the values of corresponding indexes to exchange values. For instance, in an array with length 3. Index 0 is 1 and index 2 is 3. With this code, index 0 would become 3, but there is no way for index 2 to become 1 because the value of 1 is lost forever after it has been replaced with the value of 3. So there is no way for two indexes to exchange values to reverse the array. Additionally, because the for loop loops through the entire array, after the first half of the array is set to the corresponding second half, the second half has nothing to refer to and is just set equal to the first half. 

My fix addresess the issue because it fixes the problem of not having a value to refer to after the first half has been changed. It creates a temp variable corresponding to the variable that is replaced to allow the second half of the array to reference that temp variable to set itself equal to the value that has dissapeared. My code also only loops through half the list as for each index, you can change both the first half and the second instead of having to loop through the second half. 

# Part 2 Researching Commands

## Grep Research!
**Overall Use**
`grep` searches a file for a specific pattern such as a specific word in that file, and can have additional options that determine what you want to do with that pattern such as printing where it's located etc... After running the `grep` command, it will also print out the files that you have asked it to search by, unless you use `>` which tells the program the put all the output into a text file to allow for further manipulation.

### grep -r
```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -r "base pair" plos/*.txt > basepair_plos.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepair_plos.txt
  3  48 382 basepair_plos.txt

```
**Explanation:**
`grep -r (keyword) (directory)` is an option to recursively search through all the files in a given directory that contains a certain keyword. In this case, I'm using grep to recursively look for the word "base pair" in the directory of /plos and recursively looking into every .txt file inside /plos. Additionally, I put all the files found into a .txt file and printed out the number of lines in the file to get more information. This is very useful if you have hundreds of files and you want to look through all of them to find certain keywords. Such as in this example, if we were a scientist that wanted to look for scientific research on base pairs, a good place to start would be to use grep to find which research documents include the topic of base pairs.


```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -r "terrorism" 911report/*.txt > 911reports.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc 911reports.txt
  466  5791 56093 911reports.txt
```
**Explanation:**
Similar to before, I've already described what grep -r does so now I'll describe an additional use. In this case, I use grep - r to search for every occurance of the word "terrorism" in the 911report directory. An example of using this is the real world would be if behavioral phychologists want to determine if the reoccurance of certain words during a certain event determine how people react to that event so they could search up the number of times terrorism appears in 911reports to see how the public felt about this. Additioanlly, I've used wc to get more information than waht grep could provide. nce again, grep is a useful tool however it can always be paired with other commands to become even more useful.


### grep -l
```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -l "base pair" biomed/*.txt > basepairlines.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepairlines.txt
  74   74 1966 basepairlines.txt
```
**Explanation:**
`grep -l (keyword) (directory)` recursively searches through every file in the directory and returns all the file names of files that have the keyword inside of it. In this example, I've put all the output into a textfile. I searched for all .txt files that contained the word base pair inside the biomed directory.  

```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -l "help" 911report/*.txt > 911_grepl.txt
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-12.txt
911report/chapter-13.1.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-2.txt
911report/chapter-3.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt

```
**Explanation:**
In this example, I've used the same technique but inside the 911 reports directory to recursively search for all the files that contain the word help inside that directory. This time I've left in the output and didn't put it into a file to show an example of what the grep command usually outputs. As seen here all files are .txt files and if you check, will contain the word "help".

### grep -v
```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -v "base pair" plos/*.txt > basepair_plos_non.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepair_plos_non.txt 
  38078  446279 3972219 basepair_plos_non.txt
```
**Explanation:**
`grep -v (keyword) (directory)` is the **opposite** of `grep -r` becuase instead of looking for fles that contain the keyword, it looks for files that do not the contain the keyword. We can see this as the total files found when we use `grep - v` is 38078 while with grep -r we got 3 lines. If we just use wc by itself, we would get a total of 38081 fies. That's pretty cool.


```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -v "base pair" biomed/*.txt > basepair_biomed_non.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepair_biomed_non.txt 
  490447  3925577 39157891 basepair_biomed_non.txt
```
**Explanation:**
Again, this is another example of `grep -v`. A useful application of this would be if a scientist that knows nothing about base pairs doesn't want to waste their time looking through research that has base pairs so they can use this to remove all research that has anything to do with base pairs. 


### grep -w
```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -w "hel" 911report/*.txt > hel_word.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc hel_word.txt 
0 0 0 hel_word.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -r "hel" 911report/*.txt > hel_substring.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc hel_substring.txt
  409  6702 55196 hel_substring.txt
```
**Explanation:**
`grep -w (keyword) (directory)` is used to find whole words that match the keyword in the given directory. This is especially useful when there are substrings of words that you do not want to find. As seen in the example, when we use `grep -w` with hel, since there is no such word as "hel" it returns nothing but when we do the regular `grep -r`, then we do get something because "hel" is a substring of help. 

```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -w "bas" plos/*.txt > wholeword_plos.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc wholeword_plos.txt 
0 0 0 wholeword_plos.txt
```
**Explanation:**
Once again we use this command to look for words that are only consisting of the word bas of which there are none. But if we were to use the -r option for bas, there will be options. Although it is very obvious right now why there are no files that contain "bas" as "bas" isn't a word, there are practical applications of this. Such as when there are substrings that contain a word but we want something that only contains that word by itself.


## Sources Only one source :)
1. [h](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)https://www.geeksforgeeks.org/grep-command-in-unixlinux/


















