
HIST3814o- Fail Log for Week 2

# Module 1: Exercise 1
##### Learning markdown syntax with dillinger.
### What I did
I went to [Dillinger.io][dill], opened a new browser window and began typing.
I found the annotation from Week 1 that I wanted to write about and began searching for four websites related to my topic. I came back the next day, having read all my websites, and began typing my discussion titled *The Sounds of Digital History*.  
I wrote my discussion for the exercise in [Dillinger.io][dill], exported it as a Markdown and PDF and put it in Github.
### What I learned
How to create Markdown syntax which in turn, always me to create my fail log for the course and upload it to my hist3814o-fail-log repository. 
### Failures
  - I struggled with how to insert pictures into Markdown's syntax. The text would just show up in the preview of the formatted syntax instead of a picture. To fix this, I closely followed the Markdown cheat sheet for inserting pictures. I also had to click *"view image"* when exploring the creative commons Google Images , copy that URL and insert it in the Markdown text. That corrected the issue and the images appeared.
  - I also had an issue trying to export my text, *The Sounds of Digital History*, to a PDF. I tried again the next day and it worked. 
### Thoughts
Markdown is a great program, easy to use and understand. I like how the preview of Markdown's formatted syntax appears directly to the right.
### Important
- Markdown [cheat sheet][markdown].

[markdown]: <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet> 
[dill]: <http://dillinger.io/>

# Module 1: Exercise 2
##### Getting familiar with DHBox.
### What I did
Logged into Carleton's systems via a VPN.
From my home computer I launched the application *Cisco AnyConnect Secure Mobility Client*.
I logged in with my Carleton ID.
Now I am on Carleton University's VPN. 

Went to [DHBox][dhbox]. 
Signed in with DHBox ID.
Clicked on username and went to *'apps'*.
Selected *'command line'* in your DHBox.
Logged in with DHBox ID.
Performed (without typing the *'$'* before):
```sh
$ wget https://github.com/jgm/pandoc/releases/download/1.19.2.1/pandoc-1.19.2.1-1-amd64.deb
$ sudo dpkg -i pandoc-1.19.2.1-1-amd64.deb
```
Used my password because it was sudo.
Performed: 
```sh
$ pandoc -v
$ history
$ history > dhbox-work-today.md
$ ls
$ pwd
$ nano dhbox-work-today.md
```
Result: -bash: nano: command not found
I need to install nano.
Performed:
```sh
$ sudo apt-get install nano
$ nano dhbox-work-today.md
```
Result: nano opened with the contents of dhbox-work-today.md
In Nano, I made a header at the start of the file with the date and added some text explaining what I was trying to do. Then, I hit ctrl+x to exit Nano. Nano asked if I wanted to 'Save modified buffer?'. I Hit 'y', then when it asked for the file name, I hit enter.
Used the file manager to save a copy of dhbox-work-today.md to my own computer.
Converted the markdown file into Word.
Performed: 
```sh
$ pandoc -o todayscommands.docx dhbox-work-today.md
$ ls
```
Converted the markdown file into HTML.
Performed: 
```sh
$ pandoc -o todayscommands.html dhbox-work-today.md
$ ls
```
### What I learned
How to install software into a remote computer.
How to use the *'command line'* in DHBox.
How to use *'file manager'* in DHBox.
Used pandoc to transform basic text into the more complicated formats of Word or HTML.
### Failures 
- In Nano, after I added some text, I hit ctrl+x to exit Nano. Nano asked if I wanted to 'Save modified buffer?'. I hit 'y', then when it asked for the file name, I hit enter. However, I needed to add a name file name in order to exit. When I just hit enter it kept me in Nano. 
### Thoughts
I am still unclear on what exactly DHBox does. I'm sure it will make more sense as I progress though the course. 
### Important
- A guide to using the [Nano text editor][nte].
- A cheat-sheet of keyboard shortcuts and other useful [commands for DHBox][cdhb] command-line work.

[dhbox]: <http://134.117.26.132:5000/signup> 
[nte]: <https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/> 
[cdhb]: <https://help.ubuntu.com/community/AdvancedCommandlineHowto#Keyboard_shortcuts>

# Module 1: Exercise 3
##### Setting up your github space.
### What I did
Went to Github and signed up for an account (did this during Week 1).
Logged in.
Clicked on the + at the top right of the screen, beside avatar image.
Created a new repository called *'hist3814o'*.
Wrote a short description in the 'description box', and ticked off the 'initialize the repository with a readme'. Also selected a license from the drop down box.
Clicked 'create repository'.
Once in my repository called 'hist3814o' I clicked on 'upload files'.
I dragged and dropped in the html file I created in the previous exercise, *todayscommands.html*, into the grey box to upload it into my repository.
Added a brief commit message in the commit message box (brief notes explaining why I'm making the commit).
Hit the green commit changes button.
### What I learned
Instead of creating multiple versions of a file, I can have a single file that has a version history.
For the remainder of the course, the hist3814o repository will be my scratch pad, my fail log, my open notebook, for showing my work across these modules.
### Failures 
- I put the commit message in the wrong area when adding my message for *todayscommands.html*. I put it in the 'optional extended description' when I should have put it in the area above. I am not sure how to edit this, however I corrected the issue when adding *TheSoundsofDigitalHistory.html* file.
- I was unsure exactly what the point was of this exercise and then I figured out that we were to create our fail log -what I am currently writing- in Markdown, export it to a '.md' file and then upload it into our *hist3814o* repository. 
### Thoughts
I will explore Github more to familiarize myself with the program.
### Important
- Github has a brief [tutorial][git].

From the [Workbook][workbook]:
- git is a program that keeps snapshots of the contents of a designated folder; it watches for 'difs' or differences between one snapshot and the next. You 'commit' these snapshots to a repository, which lives on your computer (it's just a folder).
- Github is a webservice that allows you to share those repositories, and to keep track of those versions online, and what's more, to share the repositories and files with multiple collaborators, and keep everyone's changes straight! There are other services that work like Github; Github is just one of the better known services. You can browse Github repositories for code that solves a particular problem for you, software, and data.

Some useful [vocabulary][workbook] when discussing git, github, and version control:
- repository: a single folder that holds all of the files and subfolders of your project
- commit: this means, 'take a snapshot of the current state of my repository'
- publish: take a folder on my computer, and copy it and its contents to the web as a repository at github.com/myusername/repositoryname
- sync: update the web repository with the latest commit from the folder on my computer
- branch: make a copy of my repository with a 'working name'
- merge: fold the changes I have made on a branch into another branch (typically, either master or gh-pages)
- fork: to make a copy of someone else's repo
- clone: to copy a repo online onto your own computer
- pull request: to ask the original maker of a repo to 'pull' your changes into their master, original, repository
- push: to move your changes from your computer to the online repo

[git]: <https://guides.github.com/activities/hello-world/>
[workbook]: <http://workbook.craftingdigitalhistory.ca/module-1/Exercises/> 

# Module 1: Exercise 4
## 4.1: git init
### What I did
Turn a folder into a repository with the git init command.
Performed:
```sh
$ mkdir first-repo
$ ls
```
Create the readme file.
```sh
$ nano readme.md
$ ls
```
Typed an explanation of what this exercise was about. Hit ctrl+x to exit, then y to save, left the file name as it is.
Performed:
```sh
$ ls
$ git init
```
### Failures
- Everything seemed to go as planned for this exercise (4.1).
## 4.2: git status
### What I did
Opened my readme.md file again with the nano text editor, from the command line. Added some more information to it, then saveed and exited the text editor.
Performed:
```sh
$ git status
$ git add -A
$ git status
```
Got something that looked like this:
```sh
On branch master
Initial commit
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   readme.md```
```
Performed:
```sh
$ git commit -m "My first commit"
```
Error.
Git will ask you for your name and email.
Performed:
```sh
$ git config --global user.email "oliviash25@aol.com"
$ git config --global user.name "Olivia"
$ git commit -m "My first commit"
```
Opened up my readme.md file again, and added some more text to it. Saved and exited the text editor. Add the new changes to the snapshot that we will take. 
```sh
$ git commit
```
Git automatically opened up the text editor so I could type a longer, more substantive commit message.Typed a message indicating the nature of the changes I have made.
Saved and exited the text editor. Did not change the filename.

## Failures
- I ended for the night. When I attempted to continue the next day, I couldn't figure out how to open my previous work in DHBox and continue from where I left off. I went under 'File Manager' and couldn't seem to figure out what file to access or how. I am going to ask the Professor and class on how to do this.
- I was also getting a little lost with DHBox and it was becoming a bit overwhelming. I was following the commands but I wasn't sure what I was doing exactly. I plan to do a bit more research on my own about how Github and DHBox work together. 
