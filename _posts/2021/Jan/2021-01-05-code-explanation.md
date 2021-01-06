---
layout: post
title: "RNA-DNA: Code Explanation"
category: truth
tags: [thoughts, coding]
author: Ramneek Narayan
---



I have finally made a through explanation for the code if anyone is curious and would like to know more. It can be useful and adapted to bioinformatics settings for more genome analysis. The code overall is a basic searching program that use built-in python operations to string match.

---

main points:

1. how to clean file to string only of letters
2. pattern matching method
3. using regex to find character positions
4. filtering results using boolean lists
5. putting condensed positions together
6. outputing to text files
7. explaining the dialogues

---


### Part 1: Cleaning the Genome

In this part, we assume that you have inputed a plain .txt file that may or may not contain spaces in it. This file is the virus' genome and could be like the following snippet:

```{python}
atcgactcgagtggatcgatgcatgcatcgatgcatgcatgcatcgatcgagctagca

cgtagcagcagtgagcagatcgaggcatgacatgcagtcggatgcagg gcatgatcg actagcat

acgattgcagtcgattgcagtgcgatgcgtgaatcggtta tacgatgc tagcatgcat gatcgataca
```

The file `clean_genomes.py` removes the new lines and spaces in between the characters. We read in the file using `.readLines()` and save the contents to a list. The list contains `\n` and blank elements for the spaces. So, if we read in the bit of code above, we get as output the list:

```{python}
ouput: ['atcgactcgagtggatcgatgcatgcatcgatgcatgcatgcatcgatcgagctagca', '\n', 'cgtagcagcagtgagcagatcgaggcatgacatgcagtcggatgcagg', ' ', 'gcatgatcg', ' ', 'actagcat', '\n', 'acgattgcagtcgattgcagtgcgatgcgtgaatcggtta', ' ', 'tacgatgc', ' ', 'tagcatgcat', '\n', 'gatcgataca']
```

Our goal is a list with one entry that is entirely a string. So, we're going to remove first the newline character '\n' from the list above using

```{python}
iter = len(genome_lines)

    for element in range(0, iter):

        base = genome_lines[element]

        base_edit = base.strip("\n")

        clean_edits.append(base_edit)

 clean_edits = list(filter(None, clean_edits))
```

this will give:

```{python}
['atcgactcgagtggatcgatgcatgcatcgatgcatgcatgcatcgatcgagctagca', 'cgtagcagcagtgagcagatcgaggcatgacatgcagtcggatgcagg', ' ', 'gcatgatcg', ' ', 'actagcat', 'acgattgcagtcgattgcagtgcgatgcgtgaatcggtta', ' ', 'tacgatgc', ' ', 'tagcatgcat', 'gatcgataca']
```

Then, we need to filter the blank spaces `' '` and this is done using the `replace()` function we will call it as `.replace(' ', '')` to say we are going to replace the space with an empty element, the code below turns `' '` into `''` for entry like `' '`. We end up with

```{python}
['atcgactcgagtggatcgatgcatgcatcgatgcatgcatgcatcgatcgagctagca', 'cgtagcagcagtgagcagatcgaggcatgacatgcagtcggatgcagg', '', 'gcatgatcg', '', 'actagcat', 'acgattgcagtcgattgcagtgcgatgcgtgaatcggtta', '', 'tacgatgc', '', 'tagcatgcat', 'gatcgataca']
```

Now we need to have one string of all the codons and we use

```{python}
''.join(str(v) for v in clean_edits)
```

The output is:

```{python}
'atcgactcgagtggatcgatgcatgcatcgatgcatgcatgcatcgatcgagctagcacgtagcagcagtgagcagatcgaggcatgacatgcagtcggatgcagggcatgatcgactagcatacgattgcagtcgattgcagtgcgatgcgtgaatcggttatacgatgctagcatgcatgatcgataca'
```

which is a string, and the cleaned genome we intended to find. This is the first part. Just for convience, we set all the capital letters to lowercase with `.lower()`.


### Part 2: Segmenting the RNA/DNA

Now that we have the cleaned genome, we have to get the 'sequence partitions' of the suspected genome (the one with spliced RNA or DNA). To do this, we use the 'snake method' where we run across the entire suspect genome one character at a time (assuming the user has given us a reasonable length) and record the subsets inside a list for comparision later. All the code that does the segmenting is given in the `sequence_matcher.py`. The code that does the sequence partitioning is given below:

```{python}
item = 0

segments_rna = [] #the empty list

if (item + splice_length) == nucleotide_count:
    segments_rna = segments_rna.append(str(suspect_genome)) #this is more robust, can also check rna of vaccines with past viral infections

else:

    while (item + splice_length) <= nucleotide_count:

        #iterate over the segments...

        sequence = suspect_genome[item:(item + splice_length)]

        #store into segments_rna list:

        segments_rna.append(sequence)

        item += 1 #increment next count
```

First we make a list called `segments_rna` that will contain the rna segements. The `if` branch is for when the user enters a splice length that's equal to the length of the genome; in that case we put the whole genome inside the rna segments and the partitioning is done. If they don't, then we go along the rna/dna segments one character at a time which is what the `while` loop does. We increment the counter for the loop or the `item` to slide along the genome. For example, suppose the suspect genome is

```{python}
cgactgatcgatc
```

then we choose a splice length of 10. The segements rna bit will have in it after the `while` loop

```{python}
segments_rna = ['cgactgatcg', 'gactgatcga', 'actgatcgat', 'ctgatcgatc']
```

This segments the rna into bits we can use to search in the viral genome.

### Part 3: Getting Search Matches

Now that we've done the searching, we're going to find matches, if any, in the viral genome we are curious about. In the code, it is called `check_genome`. The code below does the matching:

```{python}
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
```

We simply loop across the `segments_rna` list and use the `search()` function to get a regular expression output with the character locations, it is given for matches in `<...>` format. There might be no matches at all, in this case the `search()` function returns a `None` entry which we filter using `positions = list(filter(None, match_list))`. From here, we use a regular expression function `re.findall()` to extract the character positions (they come wrapped in parenthesis like '(100, 120)'). After running the code above we might get an output like:

```{python}
[None, None, <...(100,200)...>, <...(120, 220)...>, None, None]
```

After we filter the `None` and the character positions, we end up with

```{python}
['(100, 200)', '(120, 220)']
```

This tells us which character position to check for. In the code above, we will check for matches at character position '100' and '200' and also '120' and '220' in both the suspect genome and the viral genome. This gives us a long list of character matches in the form of strings '(a, b)'.

### Part 4: Filtering the Results

The long list of character matches sometimes has consecutive matches as in '(101, 121)' followed by '(102, 122)' which basically means that characters 101 to 122 are all matching and we can simplify the result as '(101, 122)'. Abstractly, this is '(a,b), (a + 1, b + 1) -> (a, b + 1)' and if we do this over and over again, we get '(a,b), (c, d) -> (a, d)' for consecutive matches leading up to 'a' to 'c'. For example, we might output

```{python}
['(515, 565)'], ['(516, 566)'], ['(517, 567)'], ['(518, 568)'], ['(519, 569)'], ['(520, 570)'], ['(521, 571)'], ['(522, 572)'], ['(523, 573)']
```

Do you notice how each pair adds one to each pair element each time? This means that the characters at position '515' to '573' are common in both genomes. And we can simplify this by outputing instead

```{python}
'(515, 573)'
```

The package does this with the `filter.py` code. We input a list of all the character matches in a nested list (called `test`), and unlist it using `test = list(chain(*test))`. To make things easier to look for in the matching, we duplicate the last element in `test` with `test.append(test[len(test)- 1])`. This is where we now have to start looking for *numbers in succession* like `2, 3, 4`. First, to simplify the searching, we focus only on the first element in the pair wrapped in the parenthesis. This is done using the code:

```{python}
iter = len(test)

    #start iterating the list

    #method:
    # extract the first entry in the tuple character: (9, 100) -> '9' and append to condensed
    #end with a list like [1, 2, 3, 4]

    for item in range(0, iter):

        trimed = str(re.findall(r'\([0-9]+',str(test[item])))
        trimed = re.findall(r'[0-9]+', trimed)
        condensed.append(int(trimed[0]))
```

which is basic regular expression parsing and appending onto an empty list called `condensed`. We then have a list like

```{python}
condensed = ['515', '516', '517', '518', '519', '520', '521', '522', '523', '523']
```

Now we have to mark the consecutive matches with a boolean list called `bool` that as a `1` prepended for matching. The idea is to go through lists like that above every 2 elements and check for a difference of `1`; this is given in the code below using the `while` loop

```{python}
bool = [1] #list of matches

    #making a simple boolean list of consecutive matches or not, 0 means no and 1 means yes
    #idea is that numbers that match have a difference of 1
    for item in range(0, iter - 1):

        if (condensed[(item + 1)] - condensed[item] == 1):
            bool.append(1)
        else:
            bool.append(0)
```

The list `bool` could look like

```{python}
bool = [1, 1, 1, 1, 1, 0, 0, 1, 0, 1, 1, 0, 1, 1, 1]
```

Notice that the entries that either end or begin a match have sums of `1` when pairing by 2 along the list, meaning we start summing from element 0 and 1, then 1 and 2, then 2 and 3, and so on until the end. We save the indicies of the ending and beginning using the code below

```{python}
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
```

we subtract one from the index due to the extra element we added in the beginning to the `test` list and if there are repeat elements, from an element that stands alone and doesn't match the next one in the very beginning, we count the list past the first item. From here, we have to store the actual matches and extract the items from the indicies in `index` and we do this with the code

```{python}
essential = []

    for item in range(0, len(index)):

        essential.append(test[index[item]]) #this will be the character lengths that can be condensed
        #there are consecutive matches here... read by each two elements, from element 1 to 2 it can
        #be condensed by consecutive matches
```

This gives us a list `essential` with pairs where the elements taken 2 at a time are the beginning and end of the results that can be simplified, essential might be:

```{python}
essential = ['(101, 121)', '(140, 160)', '(200, 220)', '(230, 250)']
```

This tells us that we have consecutive matches from position `101-160` and `200-250`. `essential` will always have an even number of elements.

All we have to do now is simplify the output using regular expressions using this part of the code:

```{python}
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
```

Which removes the extra element we added in the beginning to `test` and consequently `condensed`. Then we take the first number for every other element starting at position `0` (this goes into `first_char`) and the last number for every other element starting at position `1` (this goes into `last_char`). At this point, we put the simplified paired characters into the `last_char` list to reuse it for display.

When there are no matches at all and each item in the `test` list, we have to search for the elements that are not in consecutive order in the `condensed` list. We will search for them and put the elements inside a list called `non_slide`:

```{python}
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
```

The first two `if` statements are for the beginning and end entries. If the difference between the two beginning entries and the two end entries are not 1, then the beginning and end entries are unique and we save the indicies for them. The `for` loop then checks for the middle entries; we require the adjacent numbers to be more than 1 unit away, like `4 20 30`, then we know that `20` is unique and mark its index. From there, we append the real character positions in the last `for` loop.

The `filter.py` code is then essentially complete and a guide for what it does is like:

```{python}
'(1, 6)', '(2, 7)', '(3, 8)', '(10, 15)', '(17, 22)', '(18, 23)'

#into

'(1, 6)', '(2, 7)', '(3, 8)', '(10, 15)', '(17, 22)', '(18, 23)', '(18, 23)'

#into

'1, 2, 3, 10, 17, 18, 18'

#then, into

'1, 1, 1, 0, 0, 1, 0'

#then into, for matches

'(1, 8)', '(17, 23)'

#then into, for non-matches

'(10, 15)', '(17, 22)'
```

### Part 5: Dialogues

This part is pretty straightforward meaning we just use the `input()` function to ask for the user's file locations and open them up for reading; we also check for the user's names for the output files. We check for errors in input using the abstract `while` loop structure:

```{python}
while condition == False or condition2 == False:
    variable = input("typo, try again: ")
```

this gives an infinite loop in case of many errors. This is usually followed by `if` statements concerning the nature of the input the user gave. The `print()` function gives information about where the program is in execution as well as some feedback about what was found. Some `sleep()` statments were added to make the reading easier as well. Other than that, they are there as an aid to give inputs to the machine so it can do the analysis.

---

This is an explanation of the code with sample output and a guide to understanding what is written, perhaps for improvement and spin off ideas concerning biological analysis.

Thanks for reading and I hope you enjoy exploring genomes!

### ⨳ “think freely, anytime, anywhere.”
