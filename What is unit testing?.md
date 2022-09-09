Glen Cahilly \
Dr. Zufelt \
8 September 2022

## What is unit testing?
Simply put -- unit testing is a method for testing software.

Unit testing breaks up code into the smallest possible testable pieces (usually classes, functions, or individual lines), called 'units'. Importantly, units must be isolated -- that is, they must not rely on external systems like databases, file systems, networks, or system configurations.[^1]

The reason to use unit testing is that if bugs are found, their location is known to high precision. Instead of knowing there's an bug *somewhere* in, say, 500 lines of code, this bug would be known to be in a small class, function, or even a specific line. This makes it much easier to catch and fix bugs.

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

You test the function by comparing expected outputs to actual outputs:

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
You find that test 1 and test 2 are unsuccessful. So, there's a bug is in this function! You know the location of your program's bug (or at least, *one of the bugs*) now!

Upon further inspection, you realize it was because the line ```if dict[i] != ""``` accesses a key in the dictionary which may not exist. Now, you fix the bug and move on. You write unit tests for the rest of your functions and classes and they all pass. 

Now that you know each individual piece (or *unit*) of the function works, you're confident the program will work as a whole. You click "run" and the program works just as you'd hoped.

## Why unit test?

The main reason to use unit testing is because it allows for bugs to be easily located. Since units are *isolated*, if a function doesn't pass a unit test, the function is bugged! And, of course, it's easier to find a bug in one function than to find a bug in 20 functions!

Next, by focusing on small sections of code, it's easier to test code thoroughly. Testing large, complex blocks of code is difficult. There can be many edge cases and weird behaviors that arise. But it's easy to test small sections of code, as their behavior is less complex. Moreover, once you test each unit, you can be sure the code works as a whole!

Finally, with unit testing, one can write tests as they go. This way, bugs can be caught early and fixed before they become deeply ingrained in the code. 

[^1]: https://smartbear.com/learn/automated-testing/what-is-unit-testing/
