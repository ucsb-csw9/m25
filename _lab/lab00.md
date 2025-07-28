---
layout: lab
num: lab00
ready: true
desc: "Getting Started, Python Review"
assigned: 2025-08-04 23:59:59-7
due: 2025-08-12 23:59:59-7
---

# Introduction

Your first lab for this week is an introduction to making submissions to Gradescope's autograder and writing Python functions for review.

## Goals for this lab

By the time you have completed this lab, you should have:
* installed Python
* created and run Python progams in IDLE
* submited an assignment using the Gradescope system

# Get setup with Gradescope

We will use Gradescope to grade all your homeworks, quizzes, and lab assignments. I have manually added everyone (using your `@umail.ucsb.edu` accounts) currently enrolled in the course to the Gradescope system. You should have received an email notification with instructions about logging into Gradescope. Once you follow the instructions to set your password, you should have access to our course on Gradescope. You should see "CMPSC 9" in your Summer 2025 courses.

The lab assignment "Lab00" should appear in your Gradescope dashboard in CMPSC 9. You will need to submit your code for Lab00 using this page.

# Install Python on your computer

The instructions on installing Python on your computer can be found here:

<https://www.python.org/downloads/>

Follow the appropriate links to install Python for your computer.

# Create your Lab00 directory

It's important to be organized when working on various labs this quarter. My recommendation is to create a "cs9" folder that will contain sub folders for each lab - in this case I would recommend creating a cs9/lab00 folder on your computer where you can save your file(s) and work in this directory for Lab00. I also recommend creating a new folder for each lab assignment.

When creating or obtaining files to work with, you may use any editor of your choice. However, for now I will recommend IDLE since this comes with the installation of Python and the lab instructions will guide you through the process using IDLE (a program to create and run Python programs).

You can launch IDLE running Python 3+ as a Windows Application. On a Mac or Unix system, you can start idle by typing `idle3` in a terminal window (a program that gives us access to the `command line` interface for the computer). You can access the terminal window by opening up a terminal window:

![terminal icon](Terminal.png)

* A Terminal Window should pop up
* You can then open the IDLE program by typing `idle3`

If you are encountering any issues or need help, feel free to ask a TA / ULA for assistance when getting started.

# Create a new lab00.py file

Using the editor of your choice, create a `lab00.py` file in your lab00 directory. This `lab00.py` file will contain the python code you will submit for this lab assignment. Steps of creating this new file with IDLE are:

* Open IDLE on your computer
* Go to `File` -> `New File`, which will create an untitled file.
* Save this file by going to `File` -> `Save`, which will prompt you to save this file in a specified location.
	* Name this file `lab00` (assuming the extension will automatically be saved as a `.py` file).
	* Save this file under your cs9/lab00 directory you created for this lab.

# Copy the following code template into `lab00.py` and complete the function definitions

We will write three python functions for this lab, which reviews some of the concepts covered in CS 8 and the readings in h00.

Copy the following code into your `lab00.py` file and complete the function definitions according to the comments (and type your actual name on the first line):

```python
# Lab00, CS 9, [type your name here]

def areElementsInList(list1, list2):
    ''' This function takes two lists as its parameters (list1 and
        list2). Return True if each element in list1 exists in list2.
        Return False otherwise. If list1 contains no elements, True is
        returned.
    '''
    # COMPLETE FUNCTION DEFINITION HERE

assert areElementsInList(["one",2], [0,"one",2,"three"]) == True
assert areElementsInList([],[1,2,3,4]) == True
assert areElementsInList([1,2,3],[1,2]) == False
assert areElementsInList([1,2,3],[3,2,1]) == True

def alternateCase(s):
    ''' This function takes a string parameter (s) and returns a new
        string that flips the case of each alpha character in s.
        NOTE: Your solution **SHOULD NOT** use Python strings' swapcase()
        method (think of how you can perform this by iterating through
        each character in the string s). Hint, think of utilizing Python
        strings' isupper() and islower() methods.
    '''
    # COMPLETE FUNCTION DEFINITION HERE

assert alternateCase("") == ""
assert alternateCase("This is a Sentence") == "tHIS IS A sENTENCE"
assert alternateCase("CS9") == "cs9"
assert alternateCase("9.95") == "9.95"

def getCharacterCount(s):
    ''' This function takes a string parameter (s) and returns a dictionary
        type where each key in the dictionary is a unique upper-case character
        in s and its associated value is the number of occurences the unique
        character exists in s. Note that the unique characters should be case
        insensitive ("a" and "A" are considered the same and should be stored as
        "A" in the dictionary). Non alpha characters (including whitespaces)
        and their occurences should also be stored in the dictionary.
    '''
    # COMPLETE FUNCTION DEFINITION HERE

x = getCharacterCount("This is a Sentence")
assert x.get("S") == 3
assert x.get("P") == None
assert x.get("I") == 2
assert x.get(" ") == 3

y = getCharacterCount("Pi is Approximately 3.14159")
assert y.get("1") == 2
assert y.get("A") == 2
assert y.get("P") == 3
assert y.get(".") == 1
assert y.get(4) == None
```

Note that several `assert` statements are included after each function definition. The goal is to run your code such that these assert statements do not produce any errors and your code successfully finishes execution. Assert statements are a quick-and-dirty way to do simple testing, but there are better ways instead of just using `assert` statements scattered throughout your code for testing, which we'll cover later this quarter.

In Python, things are executed line-by-line from top to bottom. So if your code has an error and an `assert` statement doesn't pass, then you will see which `assert` statement failed and execution will stop (no other statements after the error will be executed).

In order to run your `lab00.py` file in IDLE, go to `Run` -> `Run Module`. This will start the execution of the file you're working on and the output will be displayed in IDLE's Interactive Shell.

# Submitting to Gradescope

The lab assignment "Lab00" should appear in your Gradescope dashboard in CMPSC 9. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. This prompt is shown below:

![Gradescope_upload](Gradescope_upload.png)

You either can navigate to your file(s) or "drag-and-drop" them into the "Submit Programming Assignment" window.

If you already submitted something on Gradescope, it will take you to their "Autograder Results" page. There is a "Resubmit" button on the bottom right that will allow you to update the files for your submission.

For this lab, if everything is correct, you'll see a successful submission passing all of the autograder tests shown below.

![Gradescope_results](Gradescope_results.PNG)

**Tip: Removing print statements**
If you see the following error message:

```The autograder failed to execute correctly. Please ensure that your submission is valid. Contact your course staff for help in debugging this issue. Make sure to include a link to this page so that they can help you most effectively.```

This may be because your code contains `print` statements when submitting to Gradescope. Print statements sometimes confuses the autograder resulting in this message. In general, lab submissions do not require any `print` statements (though it may be helpful to use when debugging). If you see this error, try removing any `print` statements in your code and see if that resolves your issue.

If the tests don't pass, you may get some error message that may or may not be obvious at this point. Don't worry - if the tests didn't pass, take a minute to think about what may have caused the error. If your tests didn't pass and you're still not sure why you're getting the error, feel free to ask your TAs or Learning Assistants.
