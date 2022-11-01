# text-mining

Please read the [instructions](instructions.md).



1. Project Overview [~1 paragraph] What data source(s) did you use and what technique(s) did you use analyze/process them? What did you hope to learn/create?

    I used the gutenberg data source on a book about the Seminole Indian tribe in Florida. To reach the data I copied and pasted the text from the Plain Text UTF-8 of the ebook and put it into a data folder linking it to my anlysis assignment 2 code. Similarly to the analyze_book exercise, I performed analysis on the seminole.txt that print out the total number of words, number of different words, the words in the book that aren't in the words.txt file, and 100 random words from the book.

2. Implementation [~1-2 paragraphs] Describe your implementation at a system architecture level. You should NOT walk through your code line by line, or explain every function (we can get that from your docstrings). Instead, talk about the major components, algorithms, data structures and how they fit together. You should also discuss at least one design decision where you had to choose between multiple alternatives, and explain why you made the choice you did.

    For the implementation section of this assignment, I decided to have a code that performed the same functions as the analyze book exercise we performed during session 15. So essentially their is a dictionary that is labled as "hist" and it gets passed back and forth between several functions that printo out the total number of words, the number of different words, etc. Moreover, after all these functions were written, there is a main function that runs all of the different functions and it is called so it performs them and it returns all the text analysis when I run the program.

3. Results [~2-3 paragraphs + figures/examples] Present what you accomplished:

If you did some text analysis, what interesting things did you find? Graphs or other visualizations may be very useful here for showing your results.
If you created a program that does something interesting (e.g. a Markov text synthesizer), be sure to provide a few interesting examples of the program's output.

    It took a lot of debugging to get my code to perform the correct way. It was honestly a bit silly because when I was running my program last night all the results for my text analysis read 0 because for the process_line function I forgot to return the dictionary. After I fixed this issue, the rest of my code worked for all of my functions. See below to reference the function I was talking about:

        def process_line(line, hist):
            """Adds the words in the line to the histogram.
            Modifies hist.
            line: string
            hist: histogram (map from word to frequency)
            """
            # TODO: rewrite using Counter

            # replace hyphens with spaces before splitting
            line = line.replace('-', ' ')
            strippables = string.punctuation + string.whitespace

            for word in line.split():
                # remove punctuation and convert to lowercase
                word = word.strip(strippables)
                word = word.lower()

                # update the histogram
                hist[word] = hist.get(word, 0) + 1
            return hist
    
    To elaborate on the issues I was running on, I would say that this assignment was the best debugging practice I have done this semester so far. I was able to recognize that something was wrong with my hist dictionary because all my outputs for the functions were 0. So, after every time I had code that involved hist, I  wrote "print(hist)" to see weather there was a dictionary or if it was empty. 
    
    What I found most interesting about my results was that that the most common words in the Seminole eBook would probably be the most common words in any other book. Only, 13 percent of the words were unique; meaning that they were only used once throughout the text. Also, I would like to add that the amount of words that are in this book and are not part of the english dictionary (words.txt) is higher than most other books written in the english language. This is so since the book is a history book which mentioned many differnt names, locations, and words from other languages. The only other books that I would imagine have similar ratios of most common words, unique words, and words that aren't included in the english dictionary would be other history books on pertaining to a foreign place, culture, country, or tribe.

4. Reflection [~1 paragraph] From a process point of view, what went well? What could you improve? Other possible reflection topics: Was your project appropriately scoped? Did you have a good plan for testing? How will you use what you learned going forward? What do you wish you knew before you started that would have helped you succeed?

    Based on this assignment, the thing that I was most satisfied about was that I was able to alter a previous tedious exercise with a new set of data and make it work. I was satisfied because the first time around I could not make mine operate properly. Moreover, I was able to interpret the code and understand what it was doing throughout the assignment. Although I improved my debugging skills, I could definetly improve on them even more which would have saved me a lot of time on this assignment. I also should have started this assignment earlier and that was poor time management on my part. This project was extremely useful for understanding the a potentail code architecture / structure set to use to analyze large quantities of data. It is translatable for other sets of data I would perhaps need to analyze and interpret in the future. The changes I would need to make would be to alter the current functions in the structure set to return my desired outputs. With more exercises, assignments, and practice, python will become more natural to me and I am looking forward to that time because coding would become more fun for me.