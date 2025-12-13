# filtering content

## more and less

more and less are pagers - one screen a time

search in less using /wordtosearch

cycle through search results using n and N

q to leave the pager

## head and tail

## sort

sort sorts

sort -r to reverse direction

## grep

-v to exclude results that match

## cut

cat /etc/passwd | grep -v "false\|nologin" | cut -d":" -f1

cut using delimiter ":" and  show first field

## tr - translate

replace : with space
tr ":" " "

## awk

gawk

awk programming language

parses file line by line, splits each line

print the lines that match the pattern

ls -la | awk '$5 == 4096'

ls -la | awk '$2 == 14' | wc -l

ls -la | awk '{print $1}'

ls -la | awk '{sum += $5} END {print sum}'

ls -la | awk '{print $NF}'

NF stands for last column

## sed stream editor

cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}' | sed 's/bin/HTB/g'

replace bin with HTB

