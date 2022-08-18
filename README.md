# Python-Identifying-where-file-Operations-are-required
Open and run the code in the wordcount.py script.

Double-click wordcount.py to show the source code in the editor.

This script is much shorter than before.
Much of the complexity that used to be in wordcount.py has been moved into the WordProcess class stored in the wordprocess.py file.
With the much more streamlined code and the comments in lines 9, 13, 20, 24, and 27, it would now be easier for someone new to this code get an understanding of the general flow of the program.
Run the script in wordcount.py.

If the Windows Security Console is displayed, select Allow Access.
When prompted for a file, type somefile.txt and press Enter.

The actual file name that you enter doesn't matter yet, since you haven't added code to read the input file.

At each of the two remaining prompts, enter y


Even though the program doesn't read a manuscript input file yet, a small set of manuscript words has been hardcoded into the program for testing purposes. The staged words include "four" (4 instances), "three" (3 instances), "two" (2 instances), and "one" (one instance).
Print statements starting with "TO-DO" show the five instances where you must add code to perform various file operations in the project.
In the Run window, close the wordcount tab so you have more room to view the code editor.

Examine the main script.

In line 5 of the wordcount.py code editor, select the + button so the import statements are visible.
Much of the complexity of the program has been moved out of wordcount.py. From the import statements in lines 5 and 6, you can see that wordcount.py now imports functionality from validate.py (another script containing a function named input_yesno) and wordprocess.py (the WordProcess class).
Line 10 creates the word_process object based on the WordProcess class. Then the word_process object is used in other lines to perform the various general tasks the program must accomplish: reading the input file in line 16, analyzing the input file in line 22, printing the list of word counts in line 25, and saving the list of word counts to a file in line 30.
In lines 21 and 28, much of the work involved in prompting and validating user input has been off-loaded to a new function named input_yesno. This function will repeatedly prompt the user until a proper yes or no response is provided.
Examine the new input validation function.

In line 5, double-click the function name input_yesno.


This selects the function name. PyCharm then highlights other places in the code where the selected text appears.
The function is imported from the validate module.
The function is called in lines 21 and 28 to get a validated "yes" or "no" response from the user.
In the Project pane, double-click validate.py.


The function accepts one argument, the message to be shown to the user.
Line 11 prompts the user for input, converting it to lowercase.
Line 12 checks the user's input against a list containing various acceptable responses. If the user's response is one of the acceptable responses, then line 13 is performed. If the user's response is not acceptable, then execution continues to the end of the loop, and the user will be prompted again for a response.
Line 13 evaluates whether the response is a "y" or "yes" answer, in which case, the function always returns the full response "yes". For a "n" or "no" answer, the function always returns the full response "no".
Putting a common task like this in a function makes it reusable, and also ensures that data entered by the user will be returned in a consistent form. Putting it in a separate module enables it to be easily reused in different projects.
Close the validate.py tab.

Open the file that contains the WordProcess class.

In line 10, double-click the object name word_process.

This selects the object name, so PyCharm will highlight other places where it appears.
The object is created in line 10 from the WordProcess class, and it is used in lines 16, 22, 25, and 30 to perform major tasks in the program.
In line 10, double-click the class name WordProcess.

This class contains much of the functionality that used to be in wordcount.py.

Press F4.

This PyCharm shortcut directly opens the file in which the selected class is implemented. The wordprocess.py file is shown, with the __init__ function selected. `

Note: Of course, you could also have opened the wordprocess.py file from the Project pane.

In line 5 of the wordprocess.py code editor, select the + button so the import statements are visible.

Examine the various methods implemented in the WordProcess class.

Scroll to line 15, and examine the initialization routine for the WordProcess class.


Lines 31 through 35 set the initial value of variables for a new instance (object) based on this class.
Lines 38 and 39 obtain the path and file name for wordsEn.txt, the file that contains the wordlist. The value returned from sys.path[0] is the path for the directory in which the currently running Python script is located. The requirements for the WordCount program specify that the word list file will always be stored in the program directory.
Lines 41 and 42 contain placeholder code that you must replace with code to actually read the word list file. For development and testing, for now the program manually creates a list of just four words that will be counted. Once the program can read wordsEn.txt, it will be able to look for more than 100,000 unique words.
Scroll to line 45, and examine the method that reads the input file.


This method accepts a parameter of input_file_name, which is the name of the file the user wants to read.
Line 52 keeps a copy of the input_file_name value in the object's manuscript_file property. This will enable other methods in the WordCount object to identify the name of the original file used to read in the manuscript text.
If the method reads the input manuscript file successfully, it will return a value of True. Otherwise, it will return the value False.
Lines 54 and 55 contain placeholder code that you must replace with code to actually read the input file. For development and testing, for now the program manually creates a list of ten words to simulate a very small manuscript containing 4 instances of the word "four", 3 instances of "three", 2 instances of "two", and 1 instance of "one".
Scroll to line 59, and examine the method that analyzes the input file.


This method accepts a parameter of suppress_common_words, a True or False value. If this value is True, then common words should be suppressed from the list of word counts.
After the word counts are completed (lines 66 through 77), the list is sorted (line 82), the 50 most frequently appearing words selected and (optionally) the word counts are suppressed (lines 85 through 91), the results will be contained in the object's results_list property, from which they can be printed to screen using the print_list method or saved to log files using the save_list method.
As you saw when you tested the program, the analyze method already contains the functionality required to perform the word count analysis. It will just be more useful when actual files can be processed.
Scroll to line 93, and examine the method that prints results to the screen.


Like the analyze method, the functionality for print_list is essentially complete.
Line 97 prints a message showing the name of the file that was analyzed.
Lines 98 and 99 iterate through each line in the list of results produced by the analyze method, and print them to the screen. Each line is padded with two spaces so the output will appear indented on screen.
Scroll to line 101, and examine the method that saves the results to log files.


Lines 107 and 108 identify the path to the output folder on the desktop.
Placeholders in lines 110 through 117 show where you must add code to set the output folder as the current working directory, save the results to a log file, copy the log file to a dated archive file, and list the files currently in the output folder.
If the files are saved successfully, the method returns True.
