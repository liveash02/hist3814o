HIST3814o- Fail Log for Week 4

# Module 3: Exercise 1
### Step 1: Identifying Lines that have Correspondence Senders and Receivers in them.
##### What I did
- FAIL: started in Notepad++ and was following the instructions [here][here]. Through the "Module3-help" on Slack, I realized everyone else seemed to be using the workbook instructions and so I restarted using DHBox (now that it is back up and running). Did we have an option to use either Notepad++ or DHBox. This is confusing me about the course... Too many options!
- Opened DHBox command line
- Performed:
```sh 
curl http://archive.org/stream/diplomaticcorre33statgoog/diplomaticcorre33statgoog_djvu.txt > texas.txt 

nano texas.txt
```
- I deleted everything in my working copy of the file except for the index of the list of letters ('Sam Houston to J. Pinckney Henderson, December 31, 1836 51’ and ending with ‘Wm. Henry Daingerfield to Ebenezer Allen, February 2, 1846 1582')
- I am going to keep every line that has this information in it: Sender to Recipient, Month, Date, Year, Page
- Saved it as texas2.txt
- Made a backup of my raw file and created texas3.txt as a copy to operate in
- Performed:
```sh 
liveash02@0ee73abc98e4:~$ cp texas2.txt texasbak.txt
liveash02@0ee73abc98e4:~$ cp texas2.txt texas3.txt
```
- Performed the following which added tildes (~) infront of the lines that were letters to a recipient from a sender:
```sh 
liveash02@0ee73abc98e4:~$ sed -r -i.bak 's/(.+\bto\b.+)/~\1/g' texas3.txt
liveash02@0ee73abc98e4:~$ nano texas3.txt
liveash02@0ee73abc98e4:~$ ls
texas2.txt  texas3.txt  texas3.txt.bak  texasbak.txt  texas.txt
```
- My results were correct:
```sh 
~Sam Houston to J. Pinckney Henderson, December 31, 1836 51
~James Webb to Alc6e La Branche, May 27, 1839 52
```
[here]: <https://github.com/shawngraham/hist3907o/blob/master/workbook/docs/supporting%20materials/regexex.md> 

### Step 2: Removing Lines that Aren’t Relevant.
##### What I did
- Created another copy of the file to operate in (texas4.txt) and performed the following which kept all the lines with a tildes in them:
```sh 
liveash02@0ee73abc98e4:~$ cp texas3.txt texas4.txt
liveash02@0ee73abc98e4:~$ grep '~' texas4.txt > index.txt
liveash02@0ee73abc98e4:~$ nano index.txt
```
- Results:
```sh 
~Geo. H. Flood to Jamee S. Mayfield, March 25, 1841 79
~James S. Mayfield to Geo. H. Flood, March 29, 1841 80
~Geo. H. Flood to James S. Mayfield, March 31, 1841 81
~James S. Mayfield to Barnard E. Bee, April 20, 1841 82
~James S. Mayfield to Nathaniel Amory, April 24, 1841 86
~Samuel A. Roberta to Barnard E. Bee, June 21, 1841 87
```
### Step 3: Transforming into CSV format.
##### What I did
- Next I want to turn the text file into a spreadsheet, I want to separate it out into one column for sender, one for recipient, and one for date, each separated by a single comma. 
- Created another copy of the index file to operate in (index2.txt) and performed the following which removed all the text after the year:
```sh 
liveash02@0ee73abc98e4:~$ cp index.txt index2.txt
liveash02@0ee73abc98e4:~$ sed -r -i.bak 's/(,)( [0-9]{4})(.+)/\2/g' index2.txt
liveash02@0ee73abc98e4:~$ nano index2.txt
```
- Results were correct:
```sh 
~Sam Houston to J. Pinckney Henderson, December 31 1836
~James Webb to Alc6e La Branche, May 27 1839
~David G. Burnet to Richard G. Dunlap, June 3 1839
~Nathaniel Amory to Richard G. Dunlap, July 24 1839
```
### Step 4: Removing the tildes.
##### What I did
- Created another copy of the index file to operate in (index3.txt) and performed the following:
```sh 
liveash02@0ee73abc98e4:~$ cp index2.txt index3.txt
liveash02@0ee73abc98e4:~$ sed -r -i.bak 's/~//g' index3.txt
```
- Results were correct:
```sh 
Sam Houston to J. Pinckney Henderson, December 31 1836
James Webb to Alc6e La Branche, May 27 1839
David G. Burnet to Richard G. Dunlap, June 3 1839
Nathaniel Amory to Richard G. Dunlap, July 24 1839
```
### Step 5: Separating Senders and Receivers.
##### What I did
- Performed:
```sh 
liveash02@0ee73abc98e4:~$ cp index3.txt index4.txt
liveash02@0ee73abc98e4:~$ sed -r -i.bak 's/(\b to \b)/,/g' index4.txt
liveash02@0ee73abc98e4:~$ nano index4.txt
```
- Results:
```sh 
Sam Houston,J. Pinckney Henderson, December 31 1836
James Webb,Alc6e La Branche, May 27 1839
David G. Burnet,Richard G. Dunlap, June 3 1839
Nathaniel Amory,Richard G. Dunlap, July 24 1839
```
### Step 6: Cleaning up.
##### What I did
- Performed:
```sh 
$ cp index4.txt index5.txt
$ grep -E ".+,.+,.+," index5.txt
liveash02@0ee73abc98e4:~$ nano index5.txt
```
- Edit:
```sh 
Abner S. Lipscomb,James Hamilton and A. T. Bumley, AugUHt 15, 
Address of Tilghman A. Howard,Anson Jones, between August 2 and 6, 
Eddy and Moss,the collector of the customs at New Orleans, April 23, 
A. J. Donelson,Secretary of State [Allen,. arf interim], December 10 1844
Williams, Thurston, and Meggerson,Duff Green, January 1 1845
Barnard E. Bee,James Treat, April 28, 1»40 665 
E. W. Moore,Muabeau B. Lamar, August 28, 184Q 695 
Juan de Dies Cafiedo,R. Pakenham, September 26,^.840 725 
R. Pakenham,James Treat, October 21, U540 727 
Joaquin G. Rej6n,Secretary of State [Waples, acting], January 18 1842
Joaquin G. Rei6n,Secretary of State [Waples, acting], January 18 1842
David G. Burnet,Jamee Hamilton, August 19,1839 873 
Information given by Henry J. Jewett,A. Hutchinson, February 22, 
```
- FAIL: I had to edit each line correction manually in nano which took some time. I also realized that some errors were not picked up using "GREP" such as missing dates and the second line of texts got cut off on a few occasions. 
- Corrections:

Abner S. Lipscomb,James Hamilton and A. T. Bumley, AugUHt 15, **1840**
Address of Tilghman A. Howard,Anson Jones, between August 2 and 6 **1844**
Eddy and Moss,the collector of the customs at New Orleans, April 23 **1843**
A. J. Donelson,Secretary of State [Allen*,* . arf interim], December 10 1844
Williams*,* Thurston*,* and Meggerson,Duff Green, January 1 1845
Barnard E. Bee,James Treat, April 28 **1840**
E. W. Moore,Muabeau B. Lamar, August 28 **1840**
Juan de Dies Cafiedo,R. Pakenham, September 26 **1840**
R. Pakenham,James Treat, October 21 **1840**
Joaquin G. Rej6n,Secretary of State [Waples*,* acting], January 18 1842
Joaquin G. Rei6n,Secretary of State [Waples*,* acting], January 18 1842
David G. Burnet,Jamee Hamilton, August 19*,* 1839
Information given by Henry J. Jewett,A. Hutchinson, February 22 **1841** 

- Performed:
```sh 
liveash02@0ee73abc98e4:~$ nano index5.txt
liveash02@0ee73abc98e4:~$ cp index5.txt cleaned-correspondence.csv
```

# Module 3: Exercise 2
### An Introduction to Open Refine.
##### What I did
- FAIL: I ran into difficulty downloading Openrefine. I unzipped the file but it wouldn't install on my computer. I went to https://github.com/OpenRefine/OpenRefine/releases/tag/2.7 to download the file as well and it wouldn't install either.
- I stopped here until I get feedback back from the class.
- I plan to continue this exercise.

