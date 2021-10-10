# Python for Everybody

## Chapter 01

Write a program that uses a print statement to say 'hello world' as shown in 'Desired Output'.

```
print("Hello!!")
```

## Chapter 02

2.2 Write a program that uses input to prompt a user for their name and then welcomes them.
Note that input will pop up a dialog box.
Enter Sarah in the pop-up box when you are prompted so your output will match the desired output.

```
# The code below almost works

name = input("Enter your name")
print("Hello", name)
```

2.3 Write a program to prompt the user for hours and rate per hour using input to compute gross pay.
Use 35 hours and a rate of 2.75 per hour to test the program(the pay should be 96.25).
You should use input to read a string and float() to convert the string to a number.
Do not worry about error checking or bad user data.

```
# This first line is provided for you

hrs = input("Enter Hours:")
rate = input("Enter rate of per hour")

pay = float(hrs) * float(rate)

print("Pay:", pay)
```

## Chapter 03

3.1 Write a program to prompt the user for hours and rate per hour using input to compute gross pay.
Pay the hourly rate for the hours up to 40 and 1.5 times the hourly rate for all hours worked above 40 hours.
Use 45 hours and a rate of 10.50 per hour to test the program (the pay should be 498.75).
You should use input to read a string and float() to convert the string to a number.
Do not worry about error checking the user input - assume the user types numbers properly.

```
hrs = input("Enter Hours:")
h = float(hrs)
rate = input("Enter rate:")
r = float(rate)

if h > 40 :
    sum = (40 * r) + (h - 40) * 1.5 * r
else:
    sum = h * r
    
print(sum)
```

3.3 Write a program to prompt for a score between 0.0 and 1.0.
If the score is out of range, print an error.
If the score is between 0.0 and 1.0, print a grade using the following table:
Score Grade
>= 0.9 A
>= 0.8 B
>= 0.7 C
>= 0.6 D
< 0.6 F
If the user enters a value out of range, print a suitable error message and exit. For the test, enter a score of 0.85.

```
score = input("Enter Score: ")
score = float(score)

try:
    0.0 <= score <= 1.0
except:
    print("out of range")

if score >= 0.9:
    print("A")
elif score >= 0.8:
    print("B")
elif score >= 0.7:
    print("C")
elif score >= 0.6:
    print("D")
elif score < 0.6:
    print("F")
```

## Chapter 04

4.6 Write a program to prompt the user for hours and rate per hour using input to compute gross pay.
Pay should be the normal rate for hours up to 40 and time-and-a-half for the hourly rate for all hours worked above 40 hours.
Put the logic to do the computation of pay in a function called computepay() and use the function to do the computation.
The function should return a value.
Use 45 hours and a rate of 10.50 per hour to test the program (the pay should be 498.75).
You should use input to read a string and float() to convert the string to a number.
Do not worry about error checking the user input unless you want to - you can assume the user types numbers properly.
Do not name your variable sum or use the sum() function.

```
def computepay(h, r):
    if h > 40:
        sum = (40 * r) + (h - 40) * 1.5 * r
    else:
        sum = h * r
    return sum

hrs = float(input("Enter Hours:"))
rate = float(input("Enter rates:"))

p = computepay(hrs, rate)

print("Pay", p)
```

## Chapter 05

5.2 Write a program that repeatedly prompts a user for integer numbers until the user enters 'done'.
Once 'done' is entered, print out the largest and smallest of the numbers.
If the user enters anything other than a valid number catch it with a try/except and put out an appropriate message and ignore the number.
Enter 7, 2, bob, 10, and 4 and match the output below.

```
largest = None
smallest = None

while True:
    num = input("Enter a number: ")
    if num == "done":
        break
        
    try:
        num1 = int(num)
    except:
        print("Invalid input")
        continue
    if largest is None or num1 > largest:
        largest = num1
    elif smallest is None or num1 < smallest:
        smallest = num1

print("Maximum is", largest)
print("Minimum is", smallest)
```

## Certification
![](https://images.velog.io/images/jbro321/post/036489ca-d1ef-49d8-b931-b9f96d433164/JP.jpg)

## Chapter 06

6.5 Write code using find() and string slicing (see section 6.10) to extract the number at the end of the line below.
Convert the extracted value to a floating point number and print it out.

```
text = "X-DSPAM-Confidence:    0.8475"
txt = text.find('0')
print(float(text[txt:]))
```

## Chapter 07

7.1 Write a program that prompts for a file name, then opens that file and reads through the file, and print the contents of the file in upper case.
Use the file words.txt to produce the output below.
You can download the sample data at http://www.py4e.com/code3/words.txt

```
# Use words.txt as the file name
fname = input("Enter file name: ")
fh = open(fname)
words = fh.read().rstrip().upper()

print(words)
```

7.2 Write a program that prompts for a file name, then opens that file and reads through the file, looking for lines of the form:
X-DSPAM-Confidence:    0.8475
Count these lines and extract the floating point values from each of the lines and compute the avg of those values and produce an output as shown below.
Do not use the sum() function or a variable named sum in your solution.
You can download the sample data at http://www.py4e.com/code3/mbox-short.txt when you are testing below enter mbox-short.txt as the file name.

```
# Use the file name mbox-short.txt as the file name
fname = input("Enter file name: ")
fh = open(fname)
count = 0
total = 0
for line in fh:
    if not line.startswith("X-DSPAM-Confidence:"):
        continue
    f = line.find("0")
    num = float(line[f:])
    count += 1
    total += num
    
print("Average spam confidence:", total/count)
```

## Chapter 08

8.4 Open the file romeo.txt and read it line by line.
For each line, split the line into a list of words using the split() method.
The program should build a list of words.
For each word on each line check to see if the word is already in the list and if not append it to the list.
When the program completes, sort and print the resulting words in alphabetical order.
You can download the sample data at http://www.py4e.com/code3/romeo.txt

```
fname = input("Enter file name: ")
fh = open(fname)
lst = list()
for line in fh:
    words = line.split()
    for word in words:
        if word in lst:
            continue
        lst.append(word)
    lst.sort()
print(lst)
```

8.5 Open the file mbox-short.txt and read it line by line.
When you find a line that starts with 'From ' like the following line:
From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008
You will parse the From line using split() and print out the second word in the line (i.e. the entire address of the person who sent the message).
Then print out a count at the end.
Hint: make sure not to include the lines that start with 'From:'.
Also look at the last line of the sample output to see how to print the count.

You can download the sample data at http://www.py4e.com/code3/mbox-short.txt

```
fname = input("Enter file name: ")
if len(fname) < 1:
    fname = "mbox-short.txt"

fh = open(fname)
count = 0

for line in fh:
    if not line.startswith('From'):
        continue
    if line.startswith('From:'):
        continue
    line = line.split()
    print(line[1])
    count += 1
    
print("There were",count,"lines in the file with From as the first word")
```

## Chapter 09

9.4 Write a program to read through the mbox-short.txt and figure out who has sent the greatest number of mail messages.
The program looks for 'From ' lines and takes the second word of those lines as the person who sent the mail.
The program creates a Python dictionary that maps the sender's mail address to a count of the number of times they appear in the file.
After the dictionary is produced, the program reads through the dictionary using a maximum loop to find the most prolific committer.

```
name = input('Enter File: ')
if len(name) < 1 :
    name = 'mbox-short.txt'
handle = open(name)

counts = dict()
for line in handle :
    if line.startswith('From:'):
        continue
    if line.startswith('From'):
        line = line.rstrip()
        word = line.split()
        word = word[1]
        counts[word] = counts.get(word,0) + 1  

bigcount = None
bigword = None
for word, count in counts.items():
    if bigcount is None or count > bigcount:
        bigword = word
        bigcount = count

print(bigword, bigcount)
```