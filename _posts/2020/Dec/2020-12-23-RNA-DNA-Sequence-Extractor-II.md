---
layout: post
title: "RNA-DNA Sequence Matcher II"
category: thinking
tags: reasoning
author: Ramneek Narayan
---

Over the past days, the RNA-DNA Sequence Extractor has been improved and can simplify consecutive matches as well as output .txt files for the cleaned genomes for both the suspect and virus we are interested in. I added some modularization to keep the code clean and have the entire linked folder as a python package.

> to run the code, you don't need to know python. you do need to know some basic unix directory names. that's about it. like './' means current directory, 'path/to/file.txt' has the two words before 'file.txt' as folders and the slashes open each folder. you also need to have python 3 running on your computer and simply (when in the splice_cloud folder in a terminal) type 'python3 sequence-matcher.py' and follow the dialogue.

> everyone is more than welcome to edit the code and improve it, if you see fit.

> all code needs explanation, and that is exactly my next goal but for now here's the basic idea:

#### rough idea

> 1. have 2 .txt files: virus and suspect (we think suspect has matching rna/dna in it)
> 2. scan the suspect code according to splice length according to splice length, put finger on first letter, then other finger on last letter, then slide one by one until the last finger is at the end.
> 3. put all those substrings in a list
> 4. use string operations to match the substrings in the virus, output where the match is, (start, end)
> 5. concatenate any matches right next to each other
> 6. list any matches that don't concatenate
> 7. display match results and output the cleaned genomes to a .txt file
> 8. inspect both cleaned files from locations where matches are, if any


* ideally, try different splice lengths, sometimes too large won't match, but lower ones will pick up consecutive matches and the matcher will join them. then you just have to check both files to verify.

---

I think this has great potential for computational biology and can help us find the patterns in the highly computational nature of biological code.

## The code

There are 3 parts to this formulation. The main files used are: 'clean_genomes.py', 'filter.py', and 'sequence-matcher.py'. The first one cleans the genome (a .txt file) into a plain **lowercase** and **concatenated** string, e.g. 'aababbababaabababababababab'; the second one filters the matches to simplify consecutive matches, e.g if (100, 200) and (101, 201) are present as character positions, we know that (100, 201) is also a match, like: 'abcd' and 'bcde' are all matching side by side, so we know 'abcde' is a match; the last one uses the first two to prompt you the files and display output as well as save the cleaned files to a .txt file in your working directory ('./').

Alongside and in the package there is a folder called 'text_files' which contains the sample suspect and sample virus as well as the matching spliced segment. I hope to clean and post some genomes of really popular viruses just for some ideas about how this would work in a real setting. Needless to say, most popular viral genomes can be found in data bases for those curious.

For those interested, the code in it's entirety is given below and from it, you can make a sequence matcher:

#### clean_genomes.py

```python
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

    joined_genome = joined_genome.lower() #make lowercase

    # write joined genome with all the letters to a single text file in working directory './'


    return(joined_genome)
```

#### filter.py

```python
#aims to condense certain tuples in lists...
#om a ra pa tsa na dhi
#input: list of the form: ['(1, 100)', '(2, 101)', '(3, 102)', ..., '(9, 1000)']
#output: condensed list of the form: ['(1, 102)', '(9,1000)']

import re
from re import search
from itertools import chain
from time import sleep

def my_filter(test): #test is a list of matches from sequence-matcher.py

    #test = [['(511, 561)'], ['(512, 562)'], ['(513, 563)'], ['(514, 564)'], ['(515, 565)'], ['(516, 566)'], ['(517, 567)'], ['(518, 568)'], ['(519, 569)'], ['(520, 570)'], ['(521, 571)'], ['(522, 572)'], ['(523, 573)'], ['(524, 574)'], ['(525, 575)'], ['(526, 576)'], ['(530, 580)'], ['(534, 584)'], ['(535, 585)'], ['(536, 586)'], ['(537, 587)'], ['(538, 588)'], ['(539, 589)'], ['(540, 590)'], ['(541, 591)'], ['(542, 592)'], ['(543, 593)'], ['(789, 839)'], ['(790, 840)'], ['(791, 841)'], ['(792, 842)'], ['(793, 843)'], ['(794, 844)'], ['(795, 845)'], ['(796, 846)'], ['(797, 847)'], ['(798, 848)'], ['(799, 849)'], ['(800, 850)'], ['(801, 851)'], ['(802, 852)'], ['(803, 853)'], ['(804, 854)'], ['(805, 855)'], ['(806, 856)'], ['(807, 857)'], ['(808, 858)'], ['(809, 859)'], ['(810, 860)'], ['(811, 861)'], ['(812, 862)'], ['(813, 863)'], ['(814, 864)'], ['(815, 865)'], ['(816, 866)'], ['(817, 867)'], ['(818, 868)'], ['(819, 869)'], ['(820, 870)'], ['(821, 871)'], ['(822, 872)'], ['(823, 873)'], ['(824, 874)'], ['(825, 875)'], ['(826, 876)'], ['(827, 877)'], ['(828, 878)'], ['(829, 879)'], ['(830, 880)'], ['(831, 881)'], ['(832, 882)'], ['(833, 883)'], ['(834, 884)'], ['(835, 885)'], ['(836, 886)'], ['(837, 887)'], ['(838, 888)'], ['(839, 889)'], ['(840, 890)'], ['(841, 891)'], ['(842, 892)'], ['(843, 893)'], ['(844, 894)'], ['(845, 895)'], ['(846, 896)'], ['(847, 897)'], ['(848, 898)'], ['(849, 899)'], ['(850, 900)'], ['(851, 901)'], ['(852, 902)'], ['(853, 903)'], ['(854, 904)'], ['(855, 905)'], ['(856, 906)'], ['(857, 907)'], ['(99999,9999999)'], ['(1000000, 100000000)'], ['(1000001, 100000001)']] #you can test the function using this sequence...

    test = list(chain(*test)) #unlising nested lists...

    test.append(test[len(test)- 1]) #making the end entry a duplicate of the last one
    #to force a mismatch on purpose...for counting later

    condensed = [] #condensed list, take only the first element in the tuple (a,b): extract a

    #ex: condensed = [1, 2, 3, 4, 5] or [a, b, c, d, e] for any (real) numbers a-e

    #first condense the list to first entries only...

    iter = len(test)

    #start iterating the list

    #method:
    # extract the first entry in the tuple character: (9, 100) -> '9' and append to condensed
    #end with a list like [1, 2, 3, 4]

    for item in range(0, iter):

        trimed = str(re.findall(r'\([0-9]+',str(test[item])))
        trimed = re.findall(r'[0-9]+', trimed)
        condensed.append(int(trimed[0]))



    # next we see how long consecutive numbers are...
    # input: [1, 2, 3, 4, 5, 9, 10, 11, 12, 13], then
    # maybe 1 2 3 4 5 6 7 | 200 201 202 | 300 301 302 303 304 305 | 323 324 325 326 327 328 329
    # we record indicies: 0+4, 5+9

    bool = [1] #list of matches


    #making a simple boolean list of consecutive matches or not, 0 means no and 1 means yes
    #idea is that numbers that match have a difference of 1
    for item in range(0, iter - 1):

        if (condensed[(item + 1)] - condensed[item] == 1):
            bool.append(1)
        else:
            bool.append(0)

    index = [1] #initialize with 1 for extra element

    #making a simple index recorder of the items that do match, when
    #the sum is on between consecutive list elements, we mark the either the beginning or the
    #end of the pairs that can be joined... pattern: 0 1 (beg) or 1 0 (end)
    for item_location in range(0, iter - 1):

        if (bool[item_location] + bool[item_location + 1] == 1):

            index.append(item_location + 1)
        else:
            continue

    #editing it for the indicies to use later, e.g. sequence at 11 can be joined with that in 12
    #(slide by 1 letter)
    index[:] = [x - 1 for x in index]
    #print(index)

    #index also can't have repeat elements in beginning
    if (index[0] == index[1]):
        index = index[2:]


    #print(index)
    #extract essential items from test:

    essential = []

    for item in range(0, len(index)):

        essential.append(test[index[item]]) #this will be the character lengths that can be condensed
        #there are consecutive matches here... read by each two elements, from element 1 to 2 it can
        #be condensed by consecutive matches


    #now get all unique entries...with no adjoining possible...
    #this imples a sequence like 1 2 3 4 |200| 300 301 302 |400| |450| 500 501 502...
    #200, 400, 450 are what we are trying to find

    #put the condensed matches together in a tuple form: (300,400) for (300, 350), (360, 400)
    #...

    #remove last element we added...

    del test[(len(test) - 1)]

    #first make tuples of list indices

    del condensed[len(condensed) - 1] #remove extra element we added to condensed

    # now have in easy format...

    first_char = [] #list of all of the first character positions in condensed

    for item in range(0, len(essential), 2):

        trimed = str(re.findall(r'\([0-9]+',str(essential[item])))
        trimed = re.findall(r'[0-9]+', trimed)
        first_char.append(int(trimed[0]))

    last_char = [] #list of all of the first character positions in condensed

    for item in range(1, len(essential), 2):

        trimed = str(re.findall(r'[0-9]+\)',str(essential[item])))
        trimed = re.findall(r'[0-9]+', trimed)
        last_char.append(int(trimed[0]))

    #now put the chars in coordinate form:

    for iterator in range(0, len(last_char)):

        last_char[iterator] = str([first_char[iterator], last_char[iterator]])

    #now give user dialogue about the ends that can be joined together...

    print("there were some matches that were consecutive...")
    sleep(1)
    print("we give the beginning of the match to the end of the last one... [first character, last character]")

    print(last_char)



    ########no matches part

    no_match = [] #a list of items that can't be matched, positions of the no match #note: order does not matter

    if (condensed[1] - condensed[0] != 1): #check if beginning has consecutive numbers, if not, no match
        no_match.append(0)

    if (condensed[len(condensed) - 1] - condensed[len(condensed) - 2] != 1):
        #check if end has consecutive numbers, if no, no match
        no_match.append(len(condensed) - 1)

    for pos in range(1, len(condensed) - 1):
        #check if middle entries are consecutive or not, if no, no match, always will have pattern
        # 1 0 0 1

        if (condensed[pos + 1] - condensed[pos] != 1 and condensed[pos] - condensed[pos - 1] != 1):
             no_match.append(pos)


    non_slide = []

    # get the non-matching character positions
    for pos2 in range(0, len(no_match)):

        non_slide.append(test[no_match[pos2]])

    # give the results...

    if (len(non_slide) > 0):

        sleep(2)
        print("matches that can't share the same parts are given by the character positions...")
        print(non_slide)
    else:

        print("there were no matches that were of the sequence length only once.")


    # let's test it out
```

#### sequence-matcher.py

```python
# here to see various sequences in snake order 1 2 3 4 5 | 2 3 4 5 6 | 3 4 5 6 7 and so on...
#then...detect spliced rna or just sequence matches...
#om a ra pa tsa na dhi
# author: ramneek narayan

#input: text file of genome
#output: vector of sequences, matches, dialogue if so or not...

import string
import os
from time import sleep
import re
from re import search
from filter import my_filter
from clean_genomes import clean_genome


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

    pattern_matches = len(positions)

    sleep(2)
    print("done! " + str(pattern_matches) + " matches for a " + str(splice_length) + " splice length found at character positions...")

    print(positions)

    print("the first and the last character tuples of the match are:")

    print(positions[0] + positions[(len(positions)-1)])

    print("in the virus you wished to check for spliced code.")

    #ask for filtered results (too many matches on terminal)

    sleep(1)
    print("would you like filtered results for consequtive matches?")
    ask_filter = input("the result would be (a, b), (b + 1, c + 1) -> (a, c + 1): ")

    while ask_filter != 'yes' and ask_filter != 'y' and ask_filter != 'n' and ask_filter != 'no':
        ask_filter = input("yes or no only, please: ")

    if (ask_filter == 'yes' or ask_filter == 'y'):
        sleep(0.5)
        print("filtering...")
        my_filter(positions)

    elif (ask_filter == 'no' or ask_filter == 'n'):
        sleep(0.5)
        print("won't display filtered results...")


    # now output filtered text files to user if they ask...

    # two genomes are suspect_genome and check_genome

    sus_print = input("would you like the genome for the suspect saved?: ")

    while sus_print != 'yes' and sus_print != 'y' and sus_print != 'n' and sus_print != 'no':
        ask_filter = input("yes or no only, please: ")

    sleep(0.3)
    check_print = input("would you also like the genome for the virus saved?: ")

    while check_print != 'yes' and check_print != 'y' and check_print != 'n' and check_print != 'no':
        ask_filter = input("yes or no only, please: ")


    if sus_print == 'yes' or sus_print == 'y':

        sleep(0.5)
        golden_suspect_name = input("what's the file name you want for the cleaned suspect genome?: ")
        #save to .txt extension

        golden_sus_genome = open(golden_suspect_name, "w")

        golden_sus_genome.write(suspect_genome)
        golden_sus_genome.close()
        sleep(1)
        print("saved! check ./" + str(golden_suspect_name) + " to see genome.")
        sleep(0.5)

    else:
        sleep(0.5)
        print("won't save cleaned suspect genome...")
        sleep(0.5)


    if check_print == 'yes' or check_print == 'y':

        sleep(0.5)
        golden_virus_name = input("what's the file name you want for the cleaned virus genome?: ")
        #save to .txt extension.

        golden_virus_genome = open(golden_virus_name, "w")

        golden_virus_genome.write(check_genome)
        golden_virus_genome.close()
        sleep(1)
        print("saved! check ./" + str(golden_virus_name) + " to see genome.")
        sleep(0.5)

    else:

        sleep(0.5)
        print("won't save cleaned viral genome...")
        sleep(0.5)


    if check_print == 'yes' or check_print == 'y' or sus_print == 'yes' or sus_print == 'y':

        print("happy character inspection!")

#case no matches at all
else:
    sleep(2)
    print("there were no matches for " + str(splice_length) + " splice length.")


#let's test the code:

```

The package is linked below. Happy sequence matching!

om a ra pa tsa na dhi

<a href="{{site.baseurl}}/code/splice_cloud.zip" style="font-size:18px">splice_cloud_package</a>

#### ⨳ “think freely, anytime, anywhere.”
