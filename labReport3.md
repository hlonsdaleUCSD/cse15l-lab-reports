# CSE15L Lab Report 3
## Harry Lonsdale

## Researching Commands
The command I'm choosing to research is `grep`. Let's look at some interesting command-line options for this helpful command.

## 1. -i: Case insensitivity
```
bash-3.2$ grep "eukaryotic cells" biomed/1471-2121-*-*.txt
biomed/1471-2121-2-6.txt:          activity in eukaryotic cells, and the observed effects
biomed/1471-2121-3-19.txt:          similar to the thickness in other eukaryotic cells [ 27 ]
bash-3.2$ grep -i "eukaryotic cells" biomed/1471-2121-*-*.txt
biomed/1471-2121-2-6.txt:          activity in eukaryotic cells, and the observed effects
biomed/1471-2121-3-19.txt:        Eukaryotic cells during cell division construct
biomed/1471-2121-3-19.txt:          similar to the thickness in other eukaryotic cells [ 27 ]
```
In the example here, I searched `/biomed/`'s files that's names match the pattern `1471-2121-*-*.txt` for the phrase "eukaryotic cells", first with no option, then with -i. As you can see, using -i returned more results, because the search allowed for different capitalizations. We caught an extra example in `biomed/1471-2121-3-19.txt:` that would have gone unnoticed without -i, because it begins with an uppercase E.
<br/><br/>
```
bash-3.2$ grep "research" government/Media/*.txt
government/Media/Assuring_Underprivileged.txt:"She's very thorough in her research," Wong said.
government/Media/Bias_on_the_Job.txt:to the researchers. The professors expect to make their study
government/Media/Farm_workers.txt:Little research has been conducted on the long-term health
government/Media/Farm_workers.txt:But some research points to danger: A study published earlier
government/Media/Farm_workers.txt:Recent research raises questions about the connection between
government/Media/Few_who_need.txt:of Appeal, who chaired the committee that researched and wrote the
government/Media/Good_guys_reward.txt:providing research services, mentors and continuing education - all
government/Media/Law_Schools.txt:billing, and offered free legal research and even yoga and
government/Media/Making_a_case.txt:Fridlund-Horne suggested starting by researching the specific
government/Media/Making_a_case.txt:Library research and consultation, however, are only part of
government/Media/Philly_Lawyers.txt:hard work, research, sound study and innovative thought," Gordon
government/Media/Unusual_Woodburn.txt:legal research. It also provides a salary for Samples, who speaks
government/Media/Wingates_winds.txt:If the study bears out enough facts to merit more research, the
government/Media/defend_yourself.txt:research as well.
bash-3.2$ grep -i "research" government/Media/*.txt
government/Media/Assuring_Underprivileged.txt:"She's very thorough in her research," Wong said.
government/Media/Bias_on_the_Job.txt:to the researchers. The professors expect to make their study
government/Media/Farm_workers.txt:Little research has been conducted on the long-term health
government/Media/Farm_workers.txt:But some research points to danger: A study published earlier
government/Media/Farm_workers.txt:Researchers compared farm worker data from United Farm Workers
government/Media/Farm_workers.txt:Recent research raises questions about the connection between
government/Media/Few_who_need.txt:of Appeal, who chaired the committee that researched and wrote the
government/Media/Good_guys_reward.txt:providing research services, mentors and continuing education - all
government/Media/Law_Schools.txt:billing, and offered free legal research and even yoga and
government/Media/Legal_services_for_poor.txt:Appalachian Research and Defense Fund, or APPALRED.
government/Media/Making_a_case.txt:Fridlund-Horne suggested starting by researching the specific
government/Media/Making_a_case.txt:Library research and consultation, however, are only part of
government/Media/Philly_Lawyers.txt:hard work, research, sound study and innovative thought," Gordon
government/Media/Unusual_Woodburn.txt:legal research. It also provides a salary for Samples, who speaks
government/Media/Wingates_winds.txt:If the study bears out enough facts to merit more research, the
government/Media/defend_yourself.txt:research as well.
bash-3.2$ grep "research" government/Media/*.txt | wc
      14     126    1332
bash-3.2$ grep -i "research" government/Media/*.txt | wc
      16     142    1526
```

As you can see, similarly to the first example in biomed, `-i` allowed me to find more matching results for this grep command in `government/Media` because it removed the requirement of case sensitivity. I piped the results of these grep commands into wc because it is inconvenient to count the number of lines by hand, and this shows that using -i finds us an extra 2 outputs compared to not using it.

## 2. -c: Count Matches
The -c command has the terminal print the number of occurences in each file, without printing every line in which the match occurs.
```
bash-3.2$ grep -c "cells" biomed/gb-2002-3-7-*.txt
biomed/gb-2002-3-7-research0032.txt:30
biomed/gb-2002-3-7-research0035.txt:66
biomed/gb-2002-3-7-research0036.txt:2
biomed/gb-2002-3-7-research0037.txt:6
```
Here is an example of using -c to search files that match `biomed/gb-2002-3-7-*.txt` for the word "cells". Instead of printing out every line where the word "cells" occurs, this option allows us to just see how many times the word occurs. This could be useful in some situations where we just want to know how many times it occurs, because you can save a step where you would otherwise have to use `grep` and `wc` in combination.

```
bash-3.2$ grep -c " " biomed/1471-2105-3-*.txt
biomed/1471-2105-3-12.txt:392
biomed/1471-2105-3-14.txt:1171
biomed/1471-2105-3-16.txt:775
biomed/1471-2105-3-17.txt:919
biomed/1471-2105-3-18.txt:2234
biomed/1471-2105-3-2.txt:2357
biomed/1471-2105-3-22.txt:550
biomed/1471-2105-3-23.txt:572
biomed/1471-2105-3-24.txt:216
biomed/1471-2105-3-26.txt:566
biomed/1471-2105-3-28.txt:886
biomed/1471-2105-3-3.txt:1208
biomed/1471-2105-3-30.txt:884
biomed/1471-2105-3-34.txt:600
biomed/1471-2105-3-37.txt:542
biomed/1471-2105-3-38.txt:879
biomed/1471-2105-3-4.txt:578
biomed/1471-2105-3-6.txt:799
```
This is another example of using -c to find the number of occurences in each matching file of the space character " ". This is an interesting way to use grep to quickly check the number of spaces in each `.txt` file.

## 3. `-l`: File Names Only
The command line option `-l` causes `grep` to return only the file names that have matching occurences, not the lines on which they occur. 

```
bash-3.2$ grep -l "tiger" biomed/*.txt
biomed/1472-6785-2-6.txt
```
In this example I used `grep -l` to see if any `.txt` files in biomed had the word "tiger", and as it turns out, `biomed/1472-6785-2-6.txt` does. In contrast to using grep with no option, using -l prevents the terminal from printing out every line which contains "tiger". This could be useful in case you don't want the terminal printing out every instance of the word, you just want to know which files contain it.

```
bash-3.2$ grep -l "Bin Laden" 911report/*.txt
911report/chapter-11.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-6.txt
```
This is another example of using -l to search for which files in `911report` contain the phrase "Bin Laden". Instead of needing to see every line on which the name pops up, we can just search for which files have it.

## 4. `-l`: File Names Only
The command line option `-n` causes `grep` to tell the user the line number of each match found. 

```
bash-3.2$ grep -n "imparted" biomed/*.txt
biomed/1471-213X-2-1.txt:368:        system may be imparted by an avian equivalent of PN-1.
biomed/1471-2172-3-4.txt:62:        of the hCARΔcyt transgene imparted susceptibility to
biomed/rr167.txt:567:        B is also imparted by the absence or masking of critical
```
In this example, I used `grep -n` to search every `.txt` file in biomed for the word "imparted". Grep printed not just the lines on which the word occurs, but the line numbers. This could be extremely useful if the user of the command wants to know what line number each occurence happens on, not just the content of the lines on which it occurs.
```
bash-3.2$ grep -n "shock" government/Media/*.txt
government/Media/A_helping_hand.txt:56:"I realized with a shock that the work had really disintegrated
government/Media/Towson_Attorney.txt:66:and they are injured and are in the shock trauma unit in Baltimore
```
Here's another example of using `grep -n` to find that these examples of the word "shock" happen on line 56 of `A_helping_hand.txt` and line 66 of `Towson_Attorney.txt`. Again, it can be very helpful to know this information while using `grep`. 
