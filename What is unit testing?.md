Glen Cahilly \
Dr. Zufelt \
8 September 2022

## What is unit testing?
Simply put -- unit testing is a method for testing software.

Unit testing breaks up code into the smallest possible testable pieces (usually classes, functions, or individual lines), called 'units'. Importantly, units must be isolated -- that is, they must not rely on external systems like databases, file systems, networks, or system configurations.[^1]

The idea of using unit testing is that if bugs are found, their location is known to high precision. Instead of knowing there's an bug *somewhere* in, say, 500 lines of code, this bug would be known to be in a small class, function, or even a specific line. This makes it much easier to catch and fix bugs.

## Example 1

Imagine you want to use python to manage students' schedules. Your program aims to take in a student's name and output an image of their weekly schedule. But when you complete the program and try to compile it, you get an error message. With so many different functions, you're not even sure where to start looking. 

So, you decide to use unit testing on each of your functions. The first few functions you test work fine according to your tests...

But then, you get to the function called "get_active_periods". 

```python
def get_active_periods(d)
```

## Example 2

## Why unit test?

## Sources
[^1]: https://smartbear.com/learn/automated-testing/what-is-unit-testing/
