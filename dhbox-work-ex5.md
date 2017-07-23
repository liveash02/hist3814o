    1  mkdir m2e5
    2  cd m2e5
    3  pwd
    4  pip install twarc
    5  twarc configure
    6  twarc search canada150 > search.json
    7  nano ids.txt
    8  twarc hydrate ids.txt > tweets.json
    9  nano tweets.json
   10  nano json2csv.py
   11  python json2csv.py tweets.json > out.csv
   12  history
   13  history > dhbox-work-ex5.md
