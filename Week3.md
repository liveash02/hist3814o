HIST3814o- Fail Log for Week 3

##### Comments from Professor Graham:
*"These would have been good questions to have asked in Slack. We share our successes and failures, and learn from one another. If you have these questions, I know other folks have them too. Regarding the first question - go back to the command line, and use the `cd` change directory command to change back to where you were. If you forget the name of the directory, use the `ls` command to list everything in the folder where you are; sub folders will be coloured in blue. Thus, if the folder was called `july16work` you could change directory into it with `cd july16work`. Note there is always a space after `cd`. To go up a level (to the main folder), you type `cd ..` .*

*As for the second question - Git is a program already installed on DHBox for taking those snapshots of the state of your files and folders. You tell Git which files or folders to track (with the `git add` commands), then you take the snapshot (with the `git commit`) commands. The `git log` command shows you the list of all your snapshots in reverse chronological order, and the `git checkout` command lets you turn back the clock to an earlier stage in your work."*
### What I did
- I wanted to attempt this new information from the Professor.
```sh
Documentation:  https://help.ubuntu.com/
liveash02@340ac85186e3:~$ ls
dhbox-work-today.md  first-repo  July15  pandoc-1.19.2.1-1-amd64.deb  todayscommands.docx  todayscommands.html
liveash02@340ac85186e3:~$ cd July15
-bash: cd: July15: Not a directory
liveash02@340ac85186e3:~$ cd dhbox-work-today.md
-bash: cd: dhbox-work-today.md: Not a directory
liveash02@340ac85186e3:~$ cd first-repo
liveash02@340ac85186e3:~/first-repo$ 
```

# Module 2: Exercise 1
##### The Dream Case.
### What I did
- Went to the site: http://www.cwgc.org/find-war-dead.aspx
- Searched the surname "**Ashton**"
- Got the results: http://www.cwgc.org/find-war-dead.aspx?cpage=1
"**582 record(s) match your search criteria**"
- Downloaded the CasualtySearch_22_07_2017_05_37.csv file and uploaded it to Github at https://github.com/liveash02/hist3814o
- Saved my work under dhbox-work-today2.md

# Module 2: Exercise 2
##### Wget.
### What I did
- Went to the site: [Ian Milligan's wget tutorial at the Programming Historian][wgettut]
- Followed Step 2 
- Performed:
```sh
liveash02@340ac85186e3:~/first-repo$ mkdir wget-activehistory
liveash02@340ac85186e3:~/first-repo$ cd wget-activehistory
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ wget http://activehistory.ca/papers/
--2017-07-22 18:40:46--  http://activehistory.ca/papers/
Resolving activehistory.ca (activehistory.ca)... 138.197.156.41
Connecting to activehistory.ca (activehistory.ca)|138.197.156.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘index.html’
    [ <=>                                                                                                                      ] 53,041      --.-K/s   in 0.05s   
2017-07-22 18:40:46 (1.02 MB/s) - ‘index.html’ saved [53041]
```
- Then I performed:
```sh
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ wget -r -np -w 2 -limit-rate=20k http://activehistory.ca/papers/
wget: --level: Invalid number ‘imit-rate=20k’.
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ wget -r -np -w 2 --limit-rate=20k http://activehistory.ca/papers/
--2017-07-22 19:05:13--  http://activehistory.ca/papers/
Resolving activehistory.ca (activehistory.ca)... 138.197.156.41
Connecting to activehistory.ca (activehistory.ca)|138.197.156.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘activehistory.ca/papers/index.html’
```
- ALMOST FAILURE #1: The command line started to download the pages, but I got worried thinking I did something wrong because it was taking a long time. 
- I hit "CTRL+C" like Professor said on Slack *"*if* you do end up making some sort of command that you regret, you can break out of the command by hitting ctrl+c."*
- I completed Milligan's tutorial, and put my history into a new markdown file, and lodged a copy of it in my repository.
- Performed:
```sh
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ ^C
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ history > module2exercise2.md
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ nano module2exercise2.md
```
- Saved module2exercise2.md to https://github.com/liveash02/hist3814o
- Now to download the Shawville Equity from the Quebec provincial archives
- Performed:
```sh
liveash02@340ac85186e3:~/first-repo$ mkdir equity
liveash02@340ac85186e3:~/first-repo$ cd equity
liveash02@340ac85186e3:~/first-repo/equity$ pwd
/home/liveash02/first-repo/equity
liveash02@340ac85186e3:~/first-repo/equity$ 
```
- See FAILURE #2
- Starting in 1883, I will download a decade
```sh
liveash02@340ac85186e3:~/first-repo/equity$ wget http://collections.banq.qc.ca:8008/jrn03/equity/src/1883/ -A .txt -r --no-parent -nd -w 2 --limit-rate=20k
```
- This command downloaded: 83471_1883-06-07.txt through 83471_1883-12-27.txt
- Repeated the command and changed the year to 1884, 1885, 1886, 1887, 1888, 1889, 1890, 1891, 1892, 1893
- Year 1884 command downloaded: 83471_1884-01-03.txt through 83471_1884-12-25.txt
- And so on.

### What I learned
- How to use "wget" to grab information from several different pages on a website.

### Failure
1. After I hit "CTRL+C" because I thought I performed the command wrong and was downloading everything, I watched the [video][vid] that Professor Graham suggested via Slack and realized I did exactly what I was supposed to do.
- I made sure that the command wasn't running in the background still. Then I checked out the directories.
```sh
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ ps ux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
liveash+  1182  0.0  0.0  18700  2624 pts/2    R+   20:06   0:00 ps ux
liveash+  2101  0.0  0.0  21340  3840 pts/1    S+   Jul17   0:00 -bash
liveash+ 22795  0.0  0.0  21344  3872 pts/2    S    17:11   0:00 -bash
liveash+ 23312  0.0  0.0  21340  3768 pts/0    S+   Jul15   0:00 -bash
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ ls
activehistory.ca  index.html  module2exercise2.md
liveash02@340ac85186e3:~/first-repo/wget-activehistory$ cd activehistory.ca
liveash02@340ac85186e3:~/first-repo/wget-activehistory/activehistory.ca$ ls
papers  robots.txt
liveash02@340ac85186e3:~/first-repo/wget-activehistory/activehistory.ca$ cd papers
liveash02@340ac85186e3:~/first-repo/wget-activehistory/activehistory.ca/papers$ ls
anishinaabeg-in-the-war-of-1812
bodies-of-water-not-bodies-of-women-canadian-media-images-of-the-idle-no-more-movement
canadas-first-world-war-a-centennial-series-on-activehistory-ca
commemorating-35-years-of-the-marathon-of-hope
disappearing-into-white-space-indigenous-toronto-1900-1914
historypaper-10
history-paper-5
history-papers-11
history-papers-12
history-papers-13
history-papers-14
history-papers-15
history-papers-16
index.html
index.html?share=email
indigenous-histories
paper-20
papershistory-papers-17
papershistory-papers-19
recognizing-the-historical-thinking-project
refugees-in-historical-perspective
the-contemporary-relevance-of-the-historical-treaties-to-treaty-indian-peoples
the-home-archivist
themes
theme-week-infectious-disease-contagion-and-the-history-of-vaccines
the-royal-proclamation-in-historical-context
the-social-democracy-question
truth-reconciliation-and-the-politics-of-the-body-in-indian-residential-school-history
```
2. I kept getting an error when I copied and pasted the command from the Workbook at the bottom of the exercises. For some reason, it kept changing from "*–w 2 --limit-rate=20k*" to "*aw 2 --limit-rate=20k*". I had to correct the text. 

### Thoughts 
- Moral of the story: WATCH the videos that the Professor suggests! 

[wgettut]: <https://programminghistorian.org/lessons/automated-downloading-with-wget#step-two-learning-about-the-structure-of-wget--downloading-a-specific-set-of-files>
[vid]: <https://screencast-o-matic.com/watch/cbiY2kltvy>

# Module 2: Exercise 3
##### TEI.
### Skip this for now. 

# Module 2: Exercise 4
##### APIs (application programming interface).
### What I did
- Went to the [Canadiana Discovery Portal][cdp] site
- Searched "ottawa" and set the date range to 1800 to 1900. Hit enter. 
- Searched http://search.canadiana.ca/support/api
- Added "*&fmt=json*" to the end of  "http://search.canadiana.ca/search?q=Ottawa&field=&df=1800&dt=1900" to get "http://search.canadiana.ca/search?q=Ottawa&field=&df=1800&dt=1900&fmt=json"

- Opened DHBox
- Performed:
```sh
sudo apt-get install jq -y
The following NEW packages will be installed:
  jq
liveash02@340ac85186e3:~$ mkdir m2e4
liveash02@340ac85186e3:~$ cd m2e4
liveash02@340ac85186e3:~/m2e4$ pwd
/home/liveash02/m2e4
liveash02@340ac85186e3:~/m2e4$ touch canadiana.sh
liveash02@340ac85186e3:~/m2e4$ nano canadiana.sh
```
- I copied the script below into the empty canadiana.sh. 
```sh
#! /bin/bash

pages=$(curl 'http://search.canadiana.ca/search?q=ottawa*&field=&so=score&df=1914&dt=1918&fmt=json' | jq '.pages')

# this goes into the results and reads the value of 'pages' in each one of them.
# it then tells us how many pages we're going to have.

echo "Pages:"$pages

# this says 'for each one of these pages, download the 'key' value on each page'

for i in $(seq 1 $pages)
do
        curl 'http://search.canadiana.ca/search/'${i}'?q=montenegr*&field=&so=score&df=1914&dt=1918&fmt=json' | jq '.docs[] | {key}' >> results.txt
done

# the next two lines take the results.txt file that is quite messy and clean it up. I'll try to explain what they all mean. Basically, tr deletes a given character - so we delete quotation marks "\"" (the slash tells the computer not to treat the quotation mark as a computer code, but as a quotation mark itself), to erase spaces, and to find the phrase "key:" and delete it too.

sed -e 's/\"key\": \"//g' results.txt | tr -d "\"" | tr -d "{" | tr -d "}" | tr -s " " | sed '/^\s*$/d' | tr -d ' ' > cleanlist.txt
# this adds a prefix and a suffix.

awk '$0="search.canadiana.ca/view/"$0' cleanlist.txt| awk '{print $0 "/1?r=0&s=1&fmt=json&api_text=1"}' > urlstograb.txt

# then if we want we can take those URLs and output them all to a big text file for analysis.

wget -i urlstograb.txt -O output.txt
```
- I didn't change any of the parameters because I wasn't sure if that meant the dates (1914-1918)? So I just left the script as is.
- Performed:
```sh
liveash02@340ac85186e3:~/m2e4$ chmod 755 canadiana.sh
liveash02@340ac85186e3:~/m2e4$ ./canadiana.sh
```
- Downloaded the "output.txt" file and uploaded "dhbox-work-sun23" to my repository. 
- Error: "Output.txt" too large to put into my repository (25 mb limit). Looked on Slack and saw another classmate had asked the same question "https://hist3814o.slack.com/archives/C5PEMDU3V/p1500684628113469". Made a note of the location of the file on my computer. 

### Failure
- I didn't encounter any failures in this exercise.

### Important
- 'curl', 'jq', 'sed', 'awk'. curl is a program for downloading webpages, jq for dealing with json, and sed and awk for searching within and cleaning up text.
- Introduction to [writing a program][wap]


[cdp]: <http://search.canadiana.ca/> 
[wap]: <https://williamjturkel.net/2013/06/15/basic-text-analysis-with-command-line-tools-in-linux/>

# Module 2: Exercise 5
##### Mining Twitter.
### What I did
- Used an existing Twitter account for my architecture blog.
- Went to https://apps.twitter.com/ and clicked on ‘new app’. Named my new app, gave a description and used the Crafting Digital History site url. Ticked off the box saying I’ve read the developer code of behaviour.
- Clicked on the ‘keys and access tokens’ tab. Copied the consumer key, the consumer secret to a text file. Clicked on the ‘create access tokens’ at the bottom of the page. Copied those to my text file, saved it.
- In DHBox, I performed:
```sh
liveash02@340ac85186e3:~$ mkdir m2e5
liveash02@340ac85186e3:~$ cd m2e5
liveash02@340ac85186e3:~/m2e5$ pwd
/home/liveash02/m2e5
liveash02@340ac85186e3:~/m2e5$ pip install twarc
liveash02@340ac85186e3:~/m2e5$ twarc configure
```
- I followed the annotations by my classmates and Professor Graham to remove the "sudo" text from the command
- I gave it the information it asked for (my consumer secret etc)
- Performed:
```sh
liveash02@340ac85186e3:~$ twarc search canada150 > search.json
```
- FAILURE: Did I fail if it is taking too long? I didn't get an error message so I assume that means it just takes a while to process and gather the information?
- CORRECTION: After waiting about 15 minutes, I checked my File Manager and saw a file named "*search.json*"... SUCCESS!
- I followed Professor Graham's instructions on [Slack][slack]
- Performed:
```sh
liveash02@340ac85186e3:~/m2e5$ nano ids.txt
```
- Copied the [data][data] into the "ids.txt"
- Saved and exited
- Performed:
```sh
liveash02@340ac85186e3:~/m2e5$ twarc hydrate ids.txt > tweets.json
liveash02@340ac85186e3:~/m2e5$ nano tweets.json
liveash02@340ac85186e3:~/m2e5$ nano json2csv.py
```
- I copied the code from [Twarc][twarc] into the "json2csv.py" file
- Then performed:
```sh
liveash02@340ac85186e3:~/m2e5$ python json2csv.py tweets.json > out.csv
```
- Which says *'computer! use python to run the json2csv program on the tweets.json file and push the output to a new file called out.csv'*
- Saved the "out.csv", "ids.txt", and "dhbox-work-ex5.md" files to my repository on Github


[slack]: <https://hist3814o.slack.com/files/dr.graham/F6DEUCQUF/twarc_json_to_csv__exercise_5>
[data]: <https://raw.githubusercontent.com/sarahmcole/hist3814o_module2/master/module2exercise5_tweetids.txt>
[twarc]: <https://raw.githubusercontent.com/DocNow/twarc/master/utils/json2csv.py>

##### I stopped here for this week. I still plan to do Exercise 6 tomorrow. I didn't run into any roadblocks at the moment, however I had to finish my blog post.
