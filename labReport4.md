# CSE15L Lab Report 4
## Harry Lonsdale

## SSH Keys
<br/>
These are the steps I took to fulfill steps 4-9 from the [lab writeup](https://ucsd-cse15l-s23.github.io/week/week7/#baseline)
<br/><br/>
### 1. Logging into ieng6
![Image](ssh%20into%20ieng6%20no%20password.png)
<br/><br/>
**Keys pressed**: ssh cs15lsp23gi `<shift> + 2` ieng6.ucsd.edu `<Enter>` <br/>
**Summary**: In this step I used the `ssh` command in bash to securely connect to the ieng6 server using my account. Since I set up the SSH key, I no longer need to enter a password while using this computer to do this. Very convenient!
<br/><br/><br/><br/><br/><br/><br/><br/>
### 2. Cloning my fork of the repository from my Github account
![Image](Screen%20Shot%202023-05-22%20at%202.35.28%20PM.png)
<br/><br/>
**Keys pressed**: git clone `<command> + v` `<Enter>` <br/>
**Summary**: In this step I used the git clone command to clone the repository using the ssh link that I copied from the github website. This copied the all of the files from the repository into a new directory named lab7 on the ieng6 machine.
<br/><br/>
### 3. Running the tests, demonstrating that they fail
![Image](Screen%20Shot%202023-05-22%20at%202.48.42%20PM.png)
<br/><br/>
**Keys pressed**: cd lab7 `<enter>` bash test.sh `<Enter>` <br/> 
**Summary**: In this step, I ran the command `cd` to change directory into the lab7 directory that was created through cloning. Then I run the bash script test.sh in the repository.
<br/><br/><br/><br/><br/><br/><br/><br/>
### 4. Editing the code file to fix the failing test
![Image](Screen%20Shot%202023-05-22%20at%203.02.06%20PM.png)
![Image](Screen%20Shot%202023-05-22%20at%203.04.05%20PM.png)
<br/><br/>
**Keys pressed**: vim `<Shift> + L` i `<Tab>` .java `<Enter>` 43j e r2 :wq `<Enter>` <br/>
**Summary**: In this step, I ran the command `vim` with the fileName ListExamples.java (autocompleted using tab), then pressed 43j to move 43 lines down, e to move to the end of the first word, r to replace the current character, and 2 as the character to replace 1. Then I used :wq to save the file and exit vim (yes, it's possible to exit vim. Incredible).
<br/><br/>
### 5. Running the tests, demonstrating that they now succeed
![Image](Screen%20Shot%202023-05-22%20at%203.05.45%20PM.png)
<br/><br/>
**Keys pressed**: bash test.sh `<enter>`
**Summary**: Here I just ran the tests again, the same way I did before, by using the bash script test.sh which was provided in the repository. As you can see in the screenshots, the jUnit tests no longer fail on the updated ListExamples.
<br/><br/><br/><br/><br/><br/><br/><br/>
### 6. Commiting and pushing the resulting change to my Github account 
![Image](Screen%20Shot%202023-05-22%20at%203.16.43%20PM.png)
<br/><br/>
**Keys pressed**: git add ListExamples.java `<Enter>` git commit `<Enter>` i fixed index1 to index2 `<esc>` :wq `<Enter>` git push `<Enter>`
**Summary**: In this step, I ran git add with the filename ListExamples.java to add ListExamples.java to the commit, then ran git commit to commit the changes locally. Git commit opened vim, so I entered the commit message "fixed index1 to index2" using insert mode, then exited vim using :wq. Finally, I used git push to push my changes to the remote repository on Github.
