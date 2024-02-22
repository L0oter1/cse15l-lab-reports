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

![image](https://github.com/L0oter1/cse15l-lab-reports/assets/147905421/8693f644-3e76-4e33-9aff-a9dd175bc79e)

## The Bug

**Before**

```
public class ArrayExamples {

//Changes the input array to be in reversed order
    static void reverseInPlace(int[] arr){
        for(int i = 0; i < arr.length; i+= 1){
            arr[i] = arr[arr.length -i -1];
        }
    }
}

```


**After**

```
public class ArrayExamples {

//Changes the input array to be in reversed order
    static void reverseInPlace(int[] arr){
        for(int i = 0; i < arr.length/2; i+= 1){
            int temp = arr[i];
            arr[i] = arr[arr.length - i - 1];
            arr[arr.length - i - 1] = temp;
        }
    }
}

```

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
plos/journal.pbio.0020190.txt:        sequence, which is a specific series of eight base pairs in the DNA of the bacterial
plos/journal.pbio.0020190.txt:        chromosomes, on the order of one or two thousand base pairs of DNA (or less—their length is
plos/journal.pbio.0020223.txt:        Watson-Crick base pairing, the proximity of the synthetic reactive groups elevates their
```

```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepair_plos.txt
  3  48 382 basepair_plos.txt
```

**Explanation:**
`grep -r (keyword) (directory)` is an option to recursively search through all the files in a given directory that contains a certain keyword. In this case, I'm using grep to recursively look for the word "base pair" in the directory of /plos and recursively looking into every .txt file inside /plos. Additionally, I put all the files found into a .txt file and printed out the number of lines in the file to get more information. This is very useful if you have hundreds of files and you want to look through all of them to find certain keywords. Such as in this example, if we were a scientist that wanted to look for scientific research on base pairs, a good place to start would be to use grep to find which research documents include the topic of base pairs.


```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -r "terrorism" 911report/*.txt > 911reports.txt
911report/chapter-1.txt:    At the White House, the video teleconference was conducted from the Situation Room by Richard Clarke, a special assistant to the president long involved in counterterrorism. Logs indicate that it began at 9:25 and included the CIA; the FBI; the departments of State, Justice, and Defense; the FAA; and the White House shelter. The FAA and CIA joined at 9:40. The first topic addressed in the White House video teleconference-at about 9:40-was the physical security of the President, the White House, and federal agencies. Immediately thereafter it was reported that a plane had hit the Pentagon. We found no evidence that video teleconference participants had any prior information that American 77 had been hijacked and was heading directly toward Washington. Indeed, it is not clear to us that the video teleconference was fully under way before 9:37, when the Pentagon was struck.
911report/chapter-10.txt:            In response to a request about the counterterrorism benefits of the 9/11 detainee
911report/chapter-10.txt:                links to terrorism departed on these flights.
911report/chapter-10.txt:                terrorism as a threat to our way of life," an aim that would include pursuing other
911report/chapter-10.txt:                agreed to every U.S. request for support in the war on terrorism. The next day, the
911report/chapter-10.txt:                its resources to eliminate terrorism as a threat, punish those responsible for the
911report/chapter-10.txt:                assign tasks for the first wave of the war against terrorism. It starts today."
911report/chapter-10.txt:                terrorism, not just on al Qaeda. It also incorporated the President's determination
911report/chapter-10.txt:                goal was the "elimination of terrorism as a threat to our way of life."
911report/chapter-10.txt:                striking Iraq during "this round" of the war on terrorism.
911report/chapter-10.txt:                for the war on terrorism specified three priority targets for initial action: al
911report/chapter-10.txt:                strategic threat to the United States. Iraq's long-standing involvement in terrorism
911report/chapter-10.txt:                the war on terrorism.
911report/chapter-10.txt:                terrorism, and theories that Ramzi Yousef was an Iraqi agent and Iraq was behind the
911report/chapter-10.txt:                Islamist terrorism became a different kind of struggle.
911report/chapter-11.txt:                any polling organization in the United States think the subject of terrorism
911report/chapter-11.txt:                major national survey. Bin Ladin, al Qaeda, or even terrorism was not an important
911report/chapter-11.txt:                1997 update was the last national estimate on the terrorism danger completed before
911report/chapter-11.txt:                months before 9/11:"It would be a mistake to redefine counterterrorism as a task of
911report/chapter-11.txt:                dealing with 'catastrophic,''grand,' or 'super' terrorism, when in fact these labels
911report/chapter-11.txt:                do not represent most of the terrorism that the United States is likely to face or
911report/chapter-11.txt:                most of the costs that terrorism imposes on U.S. interests."        
911report/chapter-11.txt:                none was produced on terrorism between 1997 and 9/11.
911report/chapter-11.txt:                alerts, when the nation had relaxed, Clarke held a meeting of his Counterterrorism
911report/chapter-11.txt:                warning to the CTC. An Intelligence Community Counterterrorism Board had the
911report/chapter-11.txt:                perspective ("red team" analysis), even though suicide terrorism had become a
911report/chapter-11.txt:                underestimate a threat that grew ever greater. The terrorism fostered by Bin Ladin
911report/chapter-11.txt:            Perhaps the most incisive of the advisors on terrorism to the new administration was
911report/chapter-11.txt:                State were largely ineffective. Al Qaeda and terrorism was just one more priority
911report/chapter-11.txt:                debate on counterterrorism in the Bush administration before 9/11 had to do with
911report/chapter-11.txt:                counterterrorism campaign against an enemy of this magnitude would be business
911report/chapter-11.txt:            The high price of keeping counterterrorism policy within the restricted circle of the
911report/chapter-11.txt:                Counterterrorism Security Group and the highest-level principals was nowhere more
911report/chapter-11.txt:                counterterrorism.
911report/chapter-11.txt:                this agency's role was so central in the government's counterterrorism efforts.
911report/chapter-11.txt:            The DCI did not develop a management strategy for a war against Islamist terrorism
911report/chapter-11.txt:                linked transparently to counterterrorism objectives. It would then detail the
911report/chapter-11.txt:                strategy for a war on terrorism. It was to rebuild the CIA. They said the CIA as a
911report/chapter-11.txt:                channel relatively strong outside support for combating terrorism into backing for
911report/chapter-11.txt:                across-the-board funding increases. Proponents of the counterterrorism agenda might
911report/chapter-11.txt:                if offered a convincing counterterrorism budget strategy. The DCI's management
911report/chapter-11.txt:            Lacking a management strategy for the war on terrorism or ways to see how funds were
911report/chapter-11.txt:                develop an overall intelligence community budget for a war on terrorism.
911report/chapter-11.txt:            Responsibility for domestic intelligence gathering on terrorism was vested solely in
911report/chapter-11.txt:                the counterterrorism effort was broken.
911report/chapter-11.txt:                with terrorism-the last weeks of December 1999 preceding the millennium.
911report/chapter-11.txt:                terrorism flowed widely and abundantly. The flow from the FBI was particularly
911report/chapter-11.txt:            After the millennium alert, the government relaxed. Counterterrorism went back to
911report/chapter-11.txt:                the Counterterrorism Security Group. But the experience showed that the government
911report/chapter-11.txt:                was capable of mobilizing itself for an alert against terrorism. While one factor
911report/chapter-11.txt:                Counterterrorism Security Group did their utmost to sound a loud alarm, its basis
911report/chapter-11.txt:                anyone's concern about terrorism. Front-page stories touching on the subject dealt
911report/chapter-12.txt:                our nation in this new era. The national debate continues. Countering terrorism has
911report/chapter-12.txt:                terrorism. Between fiscal year 2001, the last budget adopted before 9/11, and the
911report/chapter-12.txt:                societies than by the territorial boundaries between them. From terrorism to global
911report/chapter-12.txt:                has taught us that terrorism against American interests "over there" should be
911report/chapter-12.txt:                regarded just as we regard terrorism against America "over here." In this same
911report/chapter-12.txt:                sense, the American homeland is the planet. But the enemy is not just "terrorism,"
...
```

```
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
biomed/1471-2091-3-4.txt
biomed/1471-2105-2-8.txt
biomed/1471-2105-2-9.txt
biomed/1471-2105-3-18.txt
biomed/1471-2105-3-2.txt
biomed/1471-2105-3-24.txt
biomed/1471-2105-4-27.txt
biomed/1471-2121-1-2.txt
biomed/1471-2121-3-10.txt
biomed/1471-213X-1-4.txt
biomed/1471-2156-2-17.txt
biomed/1471-2156-2-3.txt
biomed/1471-2156-2-7.txt
biomed/1471-2156-3-16.txt
biomed/1471-2156-3-4.txt
biomed/1471-2164-2-1.txt
biomed/1471-2164-2-4.txt
biomed/1471-2164-2-7.txt
biomed/1471-2164-3-13.txt
biomed/1471-2164-3-31.txt
biomed/1471-2164-3-35.txt
biomed/1471-2164-3-6.txt
biomed/1471-2164-3-7.txt
biomed/1471-2164-4-14.txt
biomed/1471-2164-4-16.txt
biomed/1471-2164-4-2.txt
biomed/1471-2164-4-21.txt
biomed/1471-2164-4-25.txt
biomed/1471-2180-1-12.txt
biomed/1471-2180-1-31.txt
biomed/1471-2180-1-34.txt
biomed/1471-2180-2-13.txt
biomed/1471-2180-2-38.txt
biomed/1471-2180-3-13.txt
biomed/1471-2180-3-15.txt
biomed/1471-2199-2-12.txt
biomed/1471-2199-2-5.txt
...
```

```
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
$ grep -v "base pair" plos/*.txtplos/journal.pbio.0020001.txt:
plos/journal.pbio.0020001.txt:  
plos/journal.pbio.0020001.txt:    
plos/journal.pbio.0020001.txt:      
plos/journal.pbio.0020001.txt:        
plos/journal.pbio.0020001.txt:        Kofi Annan, the Secretary-General of the United Nations, recently called attention to
plos/journal.pbio.0020001.txt:        the clear inequalities in science between developing and developed countries and to the
plos/journal.pbio.0020001.txt:        challenges of building bridges across these gaps that should bring the United Nations and
plos/journal.pbio.0020001.txt:        the world scientific community closer to each other (Annan 2003). Mr. Annan stressed the
plos/journal.pbio.0020001.txt:        importance of reducing the inequalities in science between developed and developing
plos/journal.pbio.0020001.txt:        countries, asserting that “This unbalanced distribution of scientific activity generates
plos/journal.pbio.0020001.txt:        serious problems not only for the scientific community in the developing countries, but for
plos/journal.pbio.0020001.txt:        development itself.” Indeed, Mr. Annan's sentiments have also been echoed recently by
plos/journal.pbio.0020001.txt:        several scientists, who present overwhelming evidence for the disparity in scientific
plos/journal.pbio.0020001.txt:        output between the developing and already developed countries (Gibbs 1995; May 1997;
plos/journal.pbio.0020001.txt:        Goldemberg 1998; Riddoch 2000). For example, recent United Nations Educational, Scientific,
plos/journal.pbio.0020001.txt:        and Cultural Organization (UNESCO) estimates (UNESCO 2001) indicate that, in 1997, the
plos/journal.pbio.0020001.txt:        developed countries accounted for some 84% of the global investment in scientific research
plos/journal.pbio.0020001.txt:        and development, had approximately 72% of the world researchers, and produced approximately
plos/journal.pbio.0020001.txt:        88% of all scientific and technical publications registered by the Science Citation Index
plos/journal.pbio.0020001.txt:        (SCI). North America and Europe clearly dominate the number of scientific publications
plos/journal.pbio.0020001.txt:        produced annually, with 36.6% and 37.5%, respectively, worldwide (UNESCO 2001).
plos/journal.pbio.0020001.txt:        
plos/journal.pbio.0020001.txt:          
plos/journal.pbio.0020001.txt:            North America and Europe clearly dominate the number of scientific
plos/journal.pbio.0020001.txt:            publications produced annually.
plos/journal.pbio.0020001.txt:          
plos/journal.pbio.0020001.txt:        
plos/journal.pbio.0020001.txt:        It is rather obvious that richer countries are able to invest more resources in science
plos/journal.pbio.0020001.txt:        and therefore account for the largest number of publications. It is also likely that there
plos/journal.pbio.0020001.txt:        is a statistical bias on the part of the SCI as a bibliometric database, since it
plos/journal.pbio.0020001.txt:        represents North American and European publications far better than those of the rest of
plos/journal.pbio.0020001.txt:        the world (Gibbs 1995; May 1997; Alonso and Fernández-Juricic 2001; Vohora and Vohora
plos/journal.pbio.0020001.txt:        2001). But is the disparity in scientific contributions between the developed and
plos/journal.pbio.0020001.txt:        developing worlds actually remaining unchanged or even increasing, as Mr. Annan has
plos/journal.pbio.0020001.txt:        implied? A closer look at the trends over the last decade reveals important advances in
plos/journal.pbio.0020001.txt:        developing countries. For example, Latin America and China, although representing,
plos/journal.pbio.0020001.txt:        respectively, only 1.8% and 2% of scientific publications worldwide, have increased the
plos/journal.pbio.0020001.txt:        number of their publications between 1990 and 1997 by 36% and 70%, respectively, which is a
plos/journal.pbio.0020001.txt:        much higher percentage than the increments reached by Europe (10%) and industrial Asia
plos/journal.pbio.0020001.txt:        (26%). The percentage of global scientific publications from North America actually
plos/journal.pbio.0020001.txt:        decreased by 8% over the same period (UNESCO 2001).
plos/journal.pbio.0020001.txt:
...
```

```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc basepair_plos_non.txt 
  38078  446279 3972219 basepair_plos_non.txt
```

**Explanation:**
`grep -v (keyword) (directory)` is the **opposite** of `grep -r` becuase instead of looking for fles that contain the keyword, it looks for files that do not the contain the keyword. We can see this as the total files found when we use `grep - v` is 38078 while with grep -r we got 3 lines. If we just use wc by itself, we would get a total of 38081 fies. That's pretty cool.


```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -v "base pair" biomed/*.txt > basepair_biomed_non.txt
biomed/1468-6708-3-1.txt:
biomed/1468-6708-3-1.txt:  
biomed/1468-6708-3-1.txt:    
biomed/1468-6708-3-1.txt:      
biomed/1468-6708-3-1.txt:        Introduction
biomed/1468-6708-3-1.txt:        Older adults are frequently counseled to lose weight,
biomed/1468-6708-3-1.txt:        even though there is little evidence that overweight is
biomed/1468-6708-3-1.txt:        associated with increased mortality in those over age 65.
biomed/1468-6708-3-1.txt:        Six large controlled population-based studies of
biomed/1468-6708-3-1.txt:        non-smoking older adults have investigated the association
biomed/1468-6708-3-1.txt:        between body mass index (BMI) and mortality, controlling
biomed/1468-6708-3-1.txt:        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
biomed/1468-6708-3-1.txt:        excess risk for persons with very low BMI, but that persons
biomed/1468-6708-3-1.txt:        with moderately high BMI had little or no extra risk except
biomed/1468-6708-3-1.txt:        in certain small subsets. A review of 13 studies of older
biomed/1468-6708-3-1.txt:        adults drew similar conclusions [ 7 ] .
biomed/1468-6708-3-1.txt:        Many healthy older adults report gradual weight gain
biomed/1468-6708-3-1.txt:        throughout adult life. It may be that a small amount of
biomed/1468-6708-3-1.txt:        gradual weight gain is normative and associated with the
biomed/1468-6708-3-1.txt:        most robust health as we age. It has been suggested that
biomed/1468-6708-3-1.txt:        weight standards be adjusted upwards for age [ 8 ] . Such
biomed/1468-6708-3-1.txt:        recommendations remain controversial, however, because the
biomed/1468-6708-3-1.txt:        number of studies of older persons is fairly small, and
biomed/1468-6708-3-1.txt:        because few studies have examined the relation of BMI to
biomed/1468-6708-3-1.txt:        quality of life or years of healthy life (YHL) in the
biomed/1468-6708-3-1.txt:        elderly [ 9 ] .
biomed/1468-6708-3-1.txt:        In older adults, risk factors may have a greater effect
biomed/1468-6708-3-1.txt:        on health than on mortality. If so, then behavior change
biomed/1468-6708-3-1.txt:        trials of weight modification might be more successful if
biomed/1468-6708-3-1.txt:        they were evaluated on improved health, rather than on
biomed/1468-6708-3-1.txt:        decreased mortality. Clinical trials powered to detect
biomed/1468-6708-3-1.txt:        differences in YHL would often require fewer subjects than
biomed/1468-6708-3-1.txt:        trials to detect survival differences or cardiovascular
biomed/1468-6708-3-1.txt:        events [ 10 ] . In this paper we study whether BMI at
biomed/1468-6708-3-1.txt:        baseline is associated with living longer, and/or with more
biomed/1468-6708-3-1.txt:        years of being healthy, in a cohort of older adults for
biomed/1468-6708-3-1.txt:        whom risk factors, subclinical disease, and morbidity are
biomed/1468-6708-3-1.txt:        well characterized. The goal is to determine whether
biomed/1468-6708-3-1.txt:        analyses based on years of life (YOL) or on YHL would
biomed/1468-6708-3-1.txt:        provide substantively different results, and which measure
biomed/1468-6708-3-1.txt:        would yield more powerful evaluations of weight
biomed/1468-6708-3-1.txt:        modification interventions in older adults.
biomed/1468-6708-3-1.txt:      
biomed/1468-6708-3-1.txt:      

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
"Nothing outputed"

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc hel_word.txt 
0 0 0 hel_word.txt

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -r "hel" 911report/*.txt > hel_substring.txt
911report/chapter-1.txt:    When he checked in for his flight to Boston, Atta was selected by a computerized prescreening system known as CAPPS (Computer Assisted Passenger Prescreening System), created to identify passengers who should be subject to special security measures. Under security rules in place at the time, the only consequence of Atta's selection by CAPPS was that his checked bags were held off the plane until it was confirmed that he had boarded the aircraft. This did not hinder Atta's plans.
911report/chapter-1.txt:    Hani Hanjour, Khalid al Mihdhar, and Majed Moqed were flagged by CAPPS. The Hazmi brothers were also selected for extra scrutiny by the airline's customer service representative at the check-in counter. He did so because one of the brothers did not have photo identification nor could he understand English, and because the agent found both of the passengers to be suspicious. The only consequence of their selection was that their checked bags were held off the plane until it was confirmed that they had boarded the aircraft.
911report/chapter-1.txt:    The cockpit voice recorder data indicate that a woman, most likely a flight attendant, was being held captive in the cockpit. She struggled with one of the hijackers who killed or otherwise silenced her.
911report/chapter-1.txt:    The NMCC would keep the FAA hijack coordinator up to date and help the FAA centers coordinate directly with the military. NORAD would receive tracking information for the hijacked aircraft either from joint use radar or from the relevant FAA air traffic control facility. Every attempt would be made to have the hijacked aircraft squawk 7500 to help NORAD track it.
911report/chapter-1.txt:    The Herndon Command Center immediately established a teleconference between Boston, New York, and Cleveland Centers so that Boston Center could help the others understand what was happening.
911report/chapter-1.txt:    FAA: Hi. Boston Center TMU [Traffic Management Unit], we have a problem here. We have a hijacked aircraft headed towards New York, and we need you guys to, we need someone to scramble some F-16s or something up there, help us out.
911report/chapter-1.txt:    While the Command Center was told about this "other aircraft" at 9:01, New York Center contacted New York terminal approach control and asked for help in locating United 175.
911report/chapter-1.txt:    At 9:46 the Command Center updated FAA headquarters that United 93 was now "twenty-nine minutes out of Washington, D.C." At 9:49, 13 minutes after Cleveland Center had asked about getting military help, the Command Center suggested that someone at headquarters should decide whether to request military assistance: FAA Headquarters: They're pulling Jeff away to go talk about United 93.
911report/chapter-1.txt:    Thus the military did not have 14 minutes to respond to American 77, as testimony to the Commission in May 2003 suggested. It had at most one or two minutes to react to the unidentified plane approaching Washington, and the fighters were in the wrong place to be able to help. They had been responding to a report about an aircraft that did not exist.
911report/chapter-1.txt:    At the White House, Vice President Dick Cheney had just sat down for a meeting when his assistant told him to turn on his television because a plane had struck the NorthTower of the World Trade Center. The Vice President was wondering "how the hell could a plane hit the World Trade Center" when he saw the second aircraft strike the South Tower.
911report/chapter-1.txt:    At the White House, the video teleconference was conducted from the Situation Room by Richard Clarke, a special assistant to the president long involved in counterterrorism. Logs indicate that it began at 9:25 and included the CIA; the FBI; the departments of State, Justice, and Defense; the FAA; and the White House shelter. The FAA and CIA joined at 9:40. The first topic addressed in the White House video teleconference-at about 9:40-was the physical security of the President, the White House, and federal agencies. Immediately thereafter it was reported that a plane had hit the Pentagon. We found no evidence that video teleconference participants had any prior information that American 77 had been hijacked and was heading directly toward Washington. Indeed, it is not clear to us that the video teleconference was fully under way before 9:37, when the Pentagon was struck.
911report/chapter-1.txt:    It resumed at 9:37 as an air threat conference call,* which lasted more than eight hours. The President, Vice President, Secretary of Defense, Vice Chairman of the Joint Chiefs of Staff, and Deputy National Security Advisor Stephen Hadley all participated in this teleconference at various times, as did military personnel from the White House underground shelter and the President's military aide on Air Force One.
911report/chapter-1.txt:    At 9:48, a representative from the White House shelter asked if there were any indications of another hijacked aircraft. The deputy director for operations mentioned the Delta flight and concluded that "that would be the fourth possible hijack." At 9:49, the commander of NORAD directed all air sovereignty aircraft to battle stations, fully armed.
911report/chapter-1.txt:    American 77 began turning south, away from the White House, at 9:34. It continued heading south for roughly a minute, before turning west and beginning to circle back. This news prompted the Secret Service to order the immediate evacuation of the Vice President just before 9:36. Agents propelled him out of his chair and told him he had to get to the bunker. The Vice President entered the underground tunnel leading to the shelter at 9:37.
911report/chapter-1.txt:    The Secret Service logged Mrs. Cheney's arrival at the White House at 9:52, and she joined her husband in the tunnel. According to contemporaneous notes, at 9:55 the Vice President was still on the phone with the President advising that three planes were missing and one had hit the Pentagon. We believe this is the same call in which the Vice President urged the President not to return to Washington. After the call ended, Mrs. Cheney and the Vice President moved from the tunnel to the shelter conference room.
...

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc hel_substring.txt
  409  6702 55196 hel_substring.txt
```
**Explanation:**
`grep -w (keyword) (directory)` is used to find whole words that match the keyword in the given directory. This is especially useful when there are substrings of words that you do not want to find. As seen in the example, when we use `grep -w` with hel, since there is no such word as "hel" it returns nothing but when we do the regular `grep -r`, then we do get something because "hel" is a substring of help. 

```
jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ grep -w "bas" plos/*.txt > wholeword_plos.txt
"No Output"

jeffr@LAPTOP-K8R6TEJO MINGW64 ~/Downloads/docsearch-main/docsearch-main/technical
$ wc wholeword_plos.txt 
0 0 0 wholeword_plos.txt
```
**Explanation:**
Once again we use this command to look for words that are only consisting of the word bas of which there are none. But if we were to use the -r option for bas, there will be options. Although it is very obvious right now why there are no files that contain "bas" as "bas" isn't a word, there are practical applications of this. Such as when there are substrings that contain a word but we want something that only contains that word by itself.


## Sources Only one source :)
1. https://www.geeksforgeeks.org/grep-command-in-unixlinux/


















