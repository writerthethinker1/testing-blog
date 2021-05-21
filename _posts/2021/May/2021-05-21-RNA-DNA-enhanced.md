---
layout: post
title: "Updated Sequence Matcher!"
category: "logic"
tags: "reasoning"
author: Ramneek Narayan
published: true
---

Over the last couple of days, there have been some new latest and greatest improvements to the RNA-DNA sequence matcher for finding patterns between viral genomes. In terms of algorithm, nothing new has been added aside from some stylistic 'reader friendly' changes.

There is now *colour coated* terminal output as well as *directions on how to find the matches* once the code has found them. Just leaving some tips for finding effective matches...

## Tips for matches

#### 1. Choose a large number (20+) for the splice length

* to avoid any trivial matches or matches that do have any real significance as well as computation saving behaviour, it's best to use a large number for the *splice length*. It also helps with the filtration which makes the really long matches easier to find.


#### 2. When in doubt, add '1' to the matching pairs given

* depending on the text editor you use, it might count the characters starting with a '0' or a '1', and the code written assumes your text editor counts the beginning character with a '0'. most editors start with '1' for the first character, **so if you don't find a match, just increment the paired numbers by 1 and try again**. It might work then.

#### 3. Save the cleaned genomes

* if your genomes have spaces or aren't simply 1 string, then try to save them at the end to have an easier time matching the genomes.


#### 4. Make sure the file path works before you enter it!

* the program will check to see if the file exists and tell you if it doesn't, but you can avoid the hassle if you know where the file is just by using terminal commands like

  > cd path/to/genome/file.txt

  to verify it's location.

#### 5. Add the dependencies (additional packages)! Give it a test run too!

* it's in the README.md, but make sure the packages that make the program work are pre-installed using 'pip3 install [dependency]' or else it might not work. All of the dependencies are written in the 'README.md' file that comes with the package for your convenience. Once you have those, try out the package using the genome files given in the 'genomes/' folder with the suspect as 'polio' and virus as 'ebola' and splice length '40'. From there, you can try other genomes as you wish...

---

Other than that, *happy sequence matching* and enjoy learning more about genomes!!!

> Enjoy your day and make the most of life learning more and never being taken back by actions of others, events, and useless things we go through in life. Be mindful and enjoy the little things in life. Right mindfulness can help with mood and positive thinking.

Thanks for reading! You made my day, lots of warmth and energy!

<a href="{{site.baseurl}}/code/splice_1.2.zip" style="font-size:18px">splice_1.2.zip</a>

#### ⨳ “think freely, anytime, anywhere.”
