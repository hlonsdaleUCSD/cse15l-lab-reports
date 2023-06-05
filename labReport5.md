# CSE15L Lab Report 5
## Harry Lonsdale

## Edstem Bug Report

**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**
I'm using an M1 Macbook pro running commands from my terminal application window (not VS Code). 


**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

![Image](Screen%20Shot%202023-06-05%20at%2012.07.58%20PM.png)
I'm expecting to see all the lines that contain the string "Ieng6", but instead I'm getting an error message that the file labReport1.md does not exist.

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**
In the screenshot, I run wc on the labReport1 markdown file, then . My terminal is telling me that there is no such file or directory "labReport1.md", even though it clearly exists since I'm able to run `wc` on it, but not `grep`.
