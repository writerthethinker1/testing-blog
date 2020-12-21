---
layout: post
title: "RNA-DNA Sequence Matcher"
category: thinking
tags: reasoning
author: Ramneek Narayan
---

Recently with the interest of spliced DNA and recombinant DNA/RNA techniques for vaccines as well as the food we eat using GMOs, I have made a simple code checker for the sequences.

the code in it's entirety is given below, feel free to use it on various genomes:

```{python}
# here to see various sequences in snake order 1 2 3 4 5 | 2 3 4 5 6 | 3 4 5 6 7 and so on...
#then...detect spliced rna or just sequence matches...
# author: ramneek narayan

#input: text file of genome
#output: vector of sequences, matches, dialogue if so or not...

import string
import os
from time import sleep
import re
from re import search

def clean_genome(genome):

    genome_lines = genome.readlines() # a list of all the lines in the file...

    clean_edits = [] #empty list

    #get rid of any new line characters that make parsing harder...

    iter = len(genome_lines)

    for element in range(0, iter):

        base = genome_lines[element]

        base_edit = base.strip("\n")

        clean_edits.append(base_edit)


    # remove '\n' list entries

    clean_edits = list(filter(None, clean_edits))

    # remove blank spaces between list elements...

    iter2 = len(clean_edits)

    for element in range(0, iter2):

        clean_edits[element] = clean_edits[element].replace(' ', '')


    # join all the genome pieces into one...

    joined_genome = ''.join(str(v) for v in clean_edits) #this is a string of characters all joined together...

    # write joined genome with all the letters to a single text file in working directory './'


    return(joined_genome)


file_path = input("enter the suspect genome file location: ") #write the file path before using program. e.g. ~/Docs/genome.txt

#error handling for typos in file path...
while os.path.exists(file_path) == False:
    file_path = input("typo, try again: ")

suspect_genome = open(file_path,"r")

suspect_genome = clean_genome(suspect_genome)
# now we extract all the sequences for a determined length...

splice_length = input("what is the splice length?: ")

while splice_length.isdigit() == False or int(splice_length) > len(suspect_genome):
    splice_length = input("typo, enter only integers: ")

print("generating sequence partitions...")

splice_length = int(splice_length)

nucleotide_count = len(suspect_genome) #number of nucleotides...

# use a iterator to extract all sequences, sliding style...

item = 0

segments_rna = []

if (item + splice_length) == nucleotide_count:
    segments_rna = segments_rna.append(str(suspect_genome)) #this is more robust, can also check rna of vaccines with past viral infections

else:

    while (item + splice_length) <= nucleotide_count:

        #iterate over the segments...

        sequence = suspect_genome[item:(item + splice_length)]

        #store into segments_rna list:

        segments_rna.append(sequence)

        item += 1 #increment next count


# now we check the actual genome...

true_genome = input("file path of the virus you wish to check for spliced code?: ")

while os.path.exists(file_path) == False:
    file_path = input("typo, try again: ")

check_genome = open(true_genome,"r")

check_genome = clean_genome(check_genome) #a string of genome we wish to check, e.g. corona-19

# check elements of spliced_rna against check_genome:
sleep(2)
print("searching...")

match_list = []

for segment_pos in range(0, len(segments_rna)):

    check_res = search(segments_rna[segment_pos], check_genome)

    match_list.append(check_res)


# from match list, extract tuples of positions, removing 'None' and marking spans...


#now get rid of empty elements...

positions = list(filter(None, match_list))

#now get the tuples for character positions...

for item in range(0, len(positions)):

    positions[item] = re.findall(r'\(.+?\)', str(positions[item]))



# check if there are any matches...

if positions != []:

    sleep(2)
    print("done! matches for a " + str(splice_length) + " splice length found at character positions...")

    print(positions)

    print("the first and the last character tuples of the match are:")

    print(positions[0] + positions[(len(positions)-1)])

    print("in the virus you wished to check for spliced code.")

else:
    sleep(2)
    print("there were no matches for " + str(splice_length) + " splice length.")







#let's test the code:

```

Shortly, I will give explanations as to how this works for those curious as well as minor revisions.

You can download the code using this link:

<a href="{{site.baseurl}}/code/sequence-matcher.py" style="font-size:18px">sequence-extractor.py</a>
