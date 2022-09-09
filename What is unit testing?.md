Glen Cahilly \
Dr. Zufelt \
8 September 2022

## What is unit testing?
Simply put -- unit testing is a method for testing software.

Unit testing breaks up code into the smallest possible testable pieces (usually classes, functions, or individual lines), called 'units'. Importantly, units must be isolated -- that is, they must not rely on external systems like databases, file systems, networks, or system configurations.[^1]

The idea of using unit testing is that if bugs are found, their location is known to high precision. Instead of knowing there's an bug *somewhere* in, say, 500 lines of code, this bug would be known to be in a small class, function, or even a specific line. This makes it much easier to catch and fix bugs.

## Example

Imagine you want to use python to manage students' schedules. Your program aims to take in a student's name and output an image of their weekly schedule. But when you complete the program and try to compile it, you get an error message. With so many different functions, you're not even sure where to start looking. 

So, you decide to use unit testing on each of your functions. The first few functions you test work fine according to your tests...

But then, you get to the function called "get_active_periods". 

```python
# takes in dictionary relating periods to their subjects, returns list of periods that student has classes in.
# e.g. input of {1: "Math", 2: "Bio", 3: "English", 5: "Chem"} should yield output of [1, 2, 3, 5], as the 
# student has classes in periods 1, 2, 3, and 5.

def get_active_periods(dict): 
    result = []
    for i in range(8):
        if dict[i] != "":
            result.append(i)
    return result
```

You test this function like follows:

```python
def main():
    # test 1
    if get_active_periods({1: "Math") != [1]:
        print("test 1 unsuccessful!")
    
    # test 2
    if get_active_periods({1: "Math", 2: "Bio", 3: "English", 5: "Chem"}) != [1, 2, 3, 5]:
        print("test 2 unsuccessful!")
        
    # test 3
    if get_active_periods({1: "Math", 2: "Bio", 3: "English", 4: "Spanish", 5: "Chem", 6: "History", 7: "Physics"}) != [1, 2, 3, 4, 5, 6, 7]:
        print("test 3 unsuccessful!")
```
You find that test 1 and test 2 are unsuccessful. So the bug is in this function! You know the location of the bug (or at least, *one of the bugs*) now!

Upon further inspection, you realize it was because the line ```if dict[i] != ""``` accesses a key in the dictionary which may not exist. Now, you fix the bug and move on. You write unit tests for the rest of your functions and classes, and they all pass. 

## Why unit test?

## Sources
[^1]: https://smartbear.com/learn/automated-testing/what-is-unit-testing/
