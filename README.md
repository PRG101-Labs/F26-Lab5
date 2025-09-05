# PRG101-Lab5
### Submission Details

In this lab, you will create six  scripts. Write the scripts in GitHub Codespaces. 
Please note that you must complete the lab during class hours and show your progress to the professor to receive the marks for the lab.

### Lab Objectives
- To be able to read and write text files.
- To be able to process data from the file using string methods.
- To be able to handle and raise exceptions.

## INVESTIGATION 1: WORKING WITH FILES

So far, you have created Python scripts to get user's input using the input() function or taking the arguments from command line using the `sys.argv` list object. Frequently, you may also need to be able to read data from a text file and process this data, or store processed data in a file. Note that many tasks that IT professionals perform, deal with files, this is a crucial skill to learn.
In this first investigation, you will now learn how to write Python scripts that can open a text file, read the contents of the file, process the contents, and finally write the processed contents back to a file. These operations are very common, and are used extensively in programming.  Examples of file operations would include situations such as logging output, logging errors, reading and creating configuration/temporary files, etc. 
### Useful File Functions
You can use the following functions while working with files in python :

The `open()` function in Python is used to open a file in a specified mode (e.g., read 'r', write 'w', append 'a'), returning a file object for file operations.

```Python
f = open('data.txt', 'r')
```

The `read()` function in Python reads the entire content of an opened file as a string.

```Python
f.read()
```

The `readlines()` function in Python reads all lines from a file and returns them as a list of strings, where each string represents a line.

```Python
f.readlines()
```

The `readline()` function in Python reads a single line from an opened file, returning it as a string.

```Python
f.readline()
```

The `close()` function in Python is used to terminate the connection to a file.

```Python
f.close()
```

## lab5a.py
### Reading data from files
A simple way to include files in a Python program is to use the `with` statement. The header line in the code snippet below opens the file, and the block where the file can be accessed, follows. After the block, the file is automatically closed, and can no longer be accessed. The `with` statement automatically closes the file, note that there is no explicit call to the `close()` function, as this is handled by `with` statement.

```Python
with open("data.txt") as dataFile:
  data = dataFile.read()
  print(data)
Output :
Line 1
Line 2
Line 3
```

The variable `dataFile` above is a file object. We can access file contents through this file object while the file is open. Here we used the method `read()`, which returns the contents of the file as a single string. So, in this case the string returned by `read()` method would be “Line 1 \nLine 2\nLine 3”.
Text files can be thought of as lists of strings, each string representing a single line in the file. We can go through the `list` using a `for loop`.

- Create a new file called data2.txt  and paste the following text in this file:
  ```Python
  Hello World, Welcome to File Handling!	
  Line 2
  Line 3
  Line 4
  Line 5
  ```
- Complete the functions from lab5a.py according to given instructions.
- Run the script from command line using the command: python ./lab5a.py
- Take clear screenshots of the script and output. Make sure there are no empty lines in the script.

## lab5b.py
### Writing data to the files
When opening a file for writing, the 'w' option is specified as an argument to the `open()` function. When the 'w' option is specified, any previous (existing) contents inside the file are deleted. This deletion takes place the moment the `open()` function is executed, not when writing to the file. If the file doesn't exist, the file will be created upon the file opening process.

- Add the following lines in your lab5b.py to create and open a file for writing.
```Python
f = open(fruits.txt', 'w')
f.write('1. Apples are crunchy.\n2. Oranges are sweet, sour and juicy.\n3. Strawberries are sweet.\n4. Which fruit do you like?')
f.close()
print("file fruits.txt has been created")
```
- Note that the \n is the part of the string to add the new line character in the file. The `write()` method will write the contents you provide it, if you do not add \n, everything will be written as a single line.
- Run the script from terminal using the command python ./lab5b.py
- Run the `ls` command to confirm that the new file is created.
- Next add a `print` statement which prints: "Reading the file fruits.txt ...
- Next write a while loop to read the contents of the file 'fruits.txt' using the `readline()` and print each line.
- Run the script again.
- Take clear screenshots of the script and output. Make sure there are no empty lines in the script.
## lab5c.py
### Processing File data
The following Python program is creating a text-based file called rhyme.txt, which includes the lines from a children's rhyme. 
- Paste the following code in your lab4c.py file.
```Python
with open("rhyme.txt", "w") as dataFile :
  dataFile.write("I made myself a snowball\nAs perfect as could be.\nI thought I'd keep it as a pet\nAnd let it sleep with me.")
```
- Run the script using command python ./lab5c.py
- The file `rhyme.txt` should now exist with the data.
- Next in your script add code to open the file `rhyme.txt` in read mode.
- Next add a while loop and use `readline()` method to read one line at a time. While you read the line, you will process the line as well. As output print each line and the total number of words in that line in front of the line.
  -  To perform this task, you need to use the `strip()` method to get rid of white spaces from the front of the line and from the end of the line.
  -  Also remove the dot symbol using `strip()` method.
  -  Then use the `split()` method to split the line into words. The split() method returns a list of words.
  -  You can then use the `len()` function to check the length of the list.
- Close the file after processing the lines in the loop.
- The output should look like this :
```Python
I made myself a snowball --- 5 words
As perfect as could be. --- 5 words
I thought I'd keep it as a pet --- 8 words
And let it sleep with me --- 6 words
```   
- Run the script.
- Take clear screenshots of the script and output. Make sure there are no empty lines in the script.

## lab5d.py
### Processing File data
In this activity, you will be reading data from two files simultaneously and processing it.
You are given two files: `pythonStatements.txt` and `machineCode.txt`. The file `pythonStatements.txt` contains four lines and each line contains a line of code form python language. There are some spaces and the comments explaining the line of code.
The file `machineCode.txt` contains four lines of 16 digit binary code. Let's suppose that this binary code is the machine language representation of each python statement in the `pythonStatements.txt` file. The lines in both files correspond to each other. Line 1 in `machineCode.txt` is the machine code for line 1 in `pythonStatements.txt`. In the file lab5d.py write script to perform the following tasks.
- In a loop read each line from `pythonStatements.txt` and `machineCode.txt`. Remember the lines in both files correspond to each other.
- Remove all leading and trailing spaces from the line that you read from `pythonStatements.txt`, also remove the comments, so that all the is left is pure python code. The `strip()` method can be used to do this.
- Write this pure python statement with its corresponding machine code statement in a new file "output.txt".
- Add a tab between the python statement and its corresponding machine code when writing the lines.
- Run the script from command line using the command: python ./lab5d.py
- The output should be like this:
``` Python
  print("Hello World")    0000000000010100
  x = x + 1    1100110011001100
  for i in range(1,n):    1010101010101010
  calculateSum(a,b)    1001001001001000
```
- Take clear screenshots of the script and output. Make sure there are no empty lines in the script.

## INVESTIGATION 2: Exceptions and Error Handling

In this investigation, you will learn how to handle run time errors (exceptions). You were introduced to this topic in the last class of this week. In python, when a run time error occurs, python interpreter raises an exception. In this investigation, you will use exception handling mechanism i.e try-except block to handle run time errors, by gracefully quitting the program displaying a useful error message.

Remember the following points form your lesson this week:
- The try block lets you test a block of code that can generate a run time error.
- The except block lets you handle the error.
- The else block lets you execute code when there is no error.
- The finally block lets you execute code, regardless of the result of the try- and except blocks.

There are many scenarios when your script can generate run time errors, for example trying to open a file that does not exist, trying to access a folder for which you do not have permissions or simply when you are trying to convert a string into integer which cannot be converted into an integer.
Check the link: https://docs.python.org/3/library/exceptions.html#exception-hierarchy. You can see how errors get caught in python. The options FileNotFoundError, PermissionError, and IsADirectory are all inherited from OSError. This means that while using more specific errors might be useful for better error messages and handling, it's not always possible to catch every error all the time.

## lab5e.py
### Handling FileNotFoundError and ValueError 
In this activity, you will handle FileNotFoundError.
- Create a text file called ‘numbers.txt’. Add the following lines in your file.
 ```Python
 34	
 34f
 5
 6
```
- Complete the functions given in your lab4e.py file accroding to the instructions provided.
- Run the script from command line using the command: python ./lab5e.py

## lab5f.py
### Raise ZeroDivisionError
`ZeroDivisionError` in Python occurs when an attempt is made to divide a number by zero, which is mathematically undefined.
- Complete the functions given in your lab5f.py file accroding to the instructions provided.
- Run the script from command line using the command: python ./lab5f.py

## Lab 5 Sign-Off
- Submit the screenshots of each individual script, the screenshot must show your scripts and command line interface and output.
- The screenshot must also show your username on github codespaces.
- Submit individual screenshots of the following scripts on blackboard. If the screenshots do not correctly show the information mentioned above, you will get zero marks for the lab.
    - lab5a.py
    - lab5b.py
    - lab5c.py
    - lab5d.py
    - lab5e.py
    - lab5f.py
