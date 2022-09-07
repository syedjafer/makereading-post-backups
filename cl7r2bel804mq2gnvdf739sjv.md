## Code Smell 02 - Constant & Magic Numbers

### Introduction

A Magic Number is a **hard-coded** value that may change at a later stage, but that can be therefore hard to update. It's a numeric value that’s encountered in the source but has no obvious meaning.

Yet more difficulties arise when you need to change this magic number. Find and replace won’t work for this: the same number may be used for different purposes in different places, meaning that you will have to verify every line of code that uses this number.

### TL;DR: 

Do not use Magic numbers without justification. We're hesitant to modify them since we don't know where they came from.

### Explanation

A magic number is a number that **comes out of nowhere**, and is directly used in a statement. Magic numbers are often used, for instance to limit the number of iterations of a loop, to test the value of a property, etc.

Using magic numbers may seem obvious and straightforward when you’re writing a piece of code, but they are much less obvious and straightforward at debugging time.

That is why magic numbers must be demystified by first being assigned to clearly named variables before being used.

-1, 0 and 1 are not considered magic numbers.


```
def do_something():
	for itr in range(0, 4): # -> Non-compliant, 4 is a magic number.
		# Some Logic
```

In the above code, we don't know the reason of why 4 is been chosed. and it's importance. Due to this it will appear in different context to different developers. So we can't test the reason of 4; also it has low maintainability. 


**Preferred Code:**

```
NO_OF_CYCLES = 4
def do_something():
	for itr in range(0, NO_OF_CYCLES):
		# Some Logic
```

From the above code it's clear that we are dealing with NO_OF_CYCLES and has good readability and maintainability. 

### Problems

- Coupling
- Low Testability
- Low Readability

### How to fix ?

1. Rename the constant with a semantic and name (meaningful and intention revealing).
2. Replace constants with parameters, so you can mock them from outside.

### Detection

There are some linters available to check this during the development like https://eslint.org/docs/latest/rules/no-magic-numbers. Else it would get caught in code review.

### Is all magic numbers needs to hidden behind a constant ?


As an illustration, the value 86,400 should be concealed inside the constant **SECONDS_PER_DAY**. If you want to print 55 lines per page, you need hide the constant 55 behind the constant **LINES_PER_PAGE**.

Some constants are so obvious that they don't always require a named constant to conceal them, as long as they're combined with code that is quite self-explanatory. Consider this:

```
  miles_walked = feet_walked / 5280.0;
  daily_pay = hourly_rate * 8;
  circumference = radius * Math.PI * 2;
```

Do we really need the constants FEET_PER_MILE, WORK_HOURS_PER_DAY, and TWO in the above examples? 
Clearly, the last case is stupid. There are some formulae in which constants are simply better written as raw numbers. You might quibble about the WORK_HOURS_PER_DAY case because the laws or conventions might change. 

On the other hand, that formula reads so nicely with the 8 in it that I would be avoiding to add 17 extra characters (WORK_HOURS_PER_DAY) to the poor readibility. And in the FEET_PER_MILE case, the number 5280 is so very well known and so unique a constant that readers would recognize it even if it stood alone on a page with no context surrounding it.

Constants like 3.141592653589793 are also very well known and easily recognizable. However, the chance for error is too great to leave them raw. Every time someone sees 3.1415927535890793, they know what it is π, and so they fail to derive it. (Did you catch the single-digit error?) We also don’t want people using 3.14, 3.1459, 3.142, and so forth. Therefore, it is a good thing that **Math.PI** has already been defined for us.

### Need of SPOT (Single Point Of Trurth)

**If you want to change a constant value, it should be done in a single point**

Let's say you have a Page that displays the last 50 Orders in a "Your Orders" Overview Page. 50 is the Magic Number here, because it's not set through standard or convention, it's a number that you made up for reasons outlined in the spec.

Now, what you do is you have the 50 in different places - your SQL script (SELECT TOP 50 * FROM orders), your Website (Your Last 50 Orders), your order login (for (i = 0; i < 50; i++)) and possibly many other places.

Now, what happens when someone decides to change 50 to 25? or 75? or 153? You now have to replace the 50 in all the places, and you are very likely to miss it. Find/Replace may not work, because 50 may be used for other things, and blindly replacing 50 with 25 can have some other bad side effects (i.e. your Session.Timeout = 50 call, which is also set to 25 and users start reporting too frequent timeouts).

Also, the code can be hard to understand, i.e. "if a < 50 then bla" - if you encounter that in the middle of a complicated function, other developers who are not familiar with the code may ask themselves "WTF is 50???"

That's why it's best to have such ambiguous and arbitrary numbers in exactly 1 place - "NUM_OF_ORDERS_TO_DISPLAY = 50", because that makes the code more readable ("if a < NUM_OF_ORDERS_TO_DISPLAY", it also means you only need to change it in 1 well defined place.

### Final Thougths

- Don't use magic numbers without explanation. 
- Follow **SPOT**
- Do self code review with linters. 

### Quote

> In a purely functional program, the value of a [constant] never changes, and yet, it changes all the time! A paradox! - Joel Spolsky






