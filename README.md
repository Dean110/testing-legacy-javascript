# Legacy JavaScript
How to bring some ugly, scary legacy code into line and under test.  
### What you see in the real world:
Legacy JavaScript can be a really scary sight to behold when you open up your new job's codebase and take a peek at your first javascript file.  You might see a 8 year old javascript file that incorporates jQuery, depreciated functions, comments from associates (or contractors) that have left the company years ago, cut and paste code, no refactoring, or conditionals with up to 18 different logic checks.  Or maybe you'll see all of the above in one function.
### What you can do about it:
* Don't panic.
* Determine a strategy to bring this code under test.
* Write the tests to verify the code's behaviour.
* Once you are certain you have contained the behaviour of the code with a testing harness, start refactoring.
* Start to write tests to add new functionality to your code.
* Document the process for future developers to use your tests for future development of the code.
### Benefits of writing tests for Legacy Code:
- When you bring legacy code under test, you gain an intimate knowledge of what that code does.  Every line is considered and the form of the functions and the style of the project's code becomes a little less murky.  To capture the behaviour of the functions you should try to understand what they do.  This will not always be easy, some code will make you shake your head and go for a walk.  However if you stay at it, the function and behaviour of the code will become clear.  Sometimes you will find bugs hiding, waiting to be discovered.  Other times you may find 100 lines of abandoned code that can be removed.
- Once you have code under test, you get to refactor code.  The most often overlooked part of TDD is the refactoring.  Refactoring is how you can pay off technical debt.  The first time you refactor a null check for 18 variables in one `if` conditional you will be hooked!  You can confidently look at a function and extract other functions knowing that you have not damaged the code.  In fact, the code is now easier to read and change.
- You can write new functionality into the code and not worry about bad things happening.  No more copy and paste and pray, you will know that your code works because it passes it's unit tests.
### Possible Hurdles:
- Imposter syndrome:
    - 'I'm new here and this is just the way they do things.'
    - 'None of the senior developers have made changes to clean this up, why should I take the risk to lead this charge.'
- It's really scary code:
    - 'The other developers haven't made the obvious changes I see, why should I risk messing up the code that works?'
    - 'This code has been with the company longer than me, if it starts misbehaving I'm pretty sure I'm the one getting fired.'
- Office politics:
    - 'The programmers before me who wrote this worked on the project for years and this is how they must have wanted the code to work.'
    - 'I think that people on my team will think I'm wasting my time if I write tests to cover code that is already in production and has passed thousands of manual QA tests.'
### Different ways to bring JavaScript under test.
- Gold Test:
    - If the code produces a string output or an object that you can capture, this is an effective starting point.
    - You run the old code with a series of states that uses as much logic as possible to get a series of results to compare your future changed code to.  Ideally you do not want your refactoring or future changes to effect the current behaviour in an unexpected way.
    - Everytime you make a change to the code you give the new code the same states that you started with and compare it to the new output.  If there are any changes to the output, the feedback is instant.
    - This is good for code that writes long strings for reports or generates error messages.
- Testing Harness:
    - Go through the functions and write unit tests that verify the functions behavior. 
    - Anytime there is a conditional, figure out a way to test all conditions and their paths.
    - Go line by line, making sure any values that are possible to be observed have a test to observe them.
- Ideally a mixture of both would be ideal.  Imagine the tests creating a map of known behaviour for the function you are working on.  By the time you are finished you should know the size and scope of the functions footprint on the file.