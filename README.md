# JavaScript Debugging and Problem Solving

Accompanying document for this [video tutorial](https://youtu.be/SoWfKIpVvKw).

## Types of Errors

Before you get into debugging a problem, it is useful to determine what type of error you are hitting. Identifying the type of error can give you hints into what has gone wrong and how to fix it.

### Compile Errors

- These pop up when using a build step (e.g. create-react-app, webpack, etc.).
- They are errors that occur while your code is being compiled and bundled.
- They can be caused by a lot of things, but most likely you'll hit these from a broken import/export or a syntax error in your code, examples:
  - "Module not found: Can't resolve..." - this is telling you that you tried to import a file or package that could not be located.
  - "./src/components/app.js Line 64:1:  Parsing error: 'import' and 'export' may only appear at the top level" - syntax error in JS.

### Syntax Errors

- These are caused by invalid code syntax. There's something in your code that means the code cannot be fully parsed, e.g. a missing "}" in a function declaration.
- These errors will show up in VS Code as the built-in linter or the build step checks your code. They will also show up in your console within the browser.
- Examples:
  - "Uncaught SyntaxError: Identifier 'topScore' has already been declared'" - trying to redeclare a const variable.
  - "Uncaught SyntaxError: Unexpected token 'XXXXX'" - something unexpected was encountered in your syntax, usually from a missing parenthesis or curly bracket.  

### Runtime Errors:

- These are caused by an error in your code. You've written proper code syntax, but you've done something like accessing a property that doesn't exist.
- These errors will NOT show up in VS Code or in the build step. They will show up in your console within the browser.
- Examples:
  - "Uncaught TypeError: Cannot read property 'toUpper' of undefined" - calling the toUpper() method on an undefined variable.
  - "Uncaught ReferenceError: XXXXX is not defined" - attempting to access a variable that doesn't exist.

### Logical Errors:

- Your code doesn't do what you want, even though it has proper syntax and no runtime errors. These can be the trickiest to debug.
- Examples:
  - Forgetting to link a script file into the relevant HTML file. You can load the page with no errors, but nothing happens.
  - Getting the value of two number input boxes (e.g. "10" and "20") and adding them together without converting them to numbers first (e.g. "10" + "20" = "1020" instead of 10 + 20 = 30).
  
## Debugging Checklist

Something is not working! What do I do?!

- Don't stress out. Errors are a part of programming. Embrace them.
- Check for errors:
  - Check your console in Chrome. Is there an error there?
  - Check your terminal window in VS Code (if you are working on a project with a build step). Is there a compile error there?
  - Identify what type of error you are dealing with at this stage.
- Read the error messages (if you've got one):
  - Even if you don't understand every word, the words you do understand can give you clues. E.g. seeing something like "Cannot read property 'toUpper' of undefined" means you tried to access a property from a variable with a value of undefined.
  - Read the error log from top to bottom. Sometimes the first error causes a whole slew of additional errors, and solving the first one cascades out and fixes others.
  - Use the files and line numbers from the error messages to start your hunt for the problem.
  - Google the error message. You won't find the exact solution to your situation, but it will give you clues and things to test. Use the appropriate keywords, e.g. "JavaScript" or "JavaScript React."
- Locate and isolate:
  - Comment out, disable, inactivate, etc. as much as you can until your game is in a working state again.
  - Re-introduce things piece by piece until you find the element that is introducing the bug.
  - Repeat until all bugs are fixed.
- Use the developer tools:
  - The almighty debugger. This allows you to trace the path your code takes and check each variable along the way. Drop a breakpoint near where you expect the problem is occurring. Verify that each line is giving you the result you expect.
  - Drop in console.log to check the state of variables and trace the path your code takes. The debugger is usually a better choice, but console.log is helpful when you want to see the state of something while your code is running in realtime.
- Reach out:
  - Your peers in class, your instructors, stack overflow, etc.
  - Even a [rubber duck](https://rubberduckdebugging.com/) works!
  - The simple act of writing up or articulating your problem actually helps you question your assumptions and see your problem in a new light. You will often solve the problem yourself just through explaining it to someone else.
- Take a breath and a break:
  - Get up and walk around, take a nap, focus on something else for a bit.
  - After your break, come back to the problem.
  - Sometimes, all you need is [fresh eyes](https://psychology.stackexchange.com/questions/1/how-is-it-that-taking-a-break-from-a-problem-sometimes-allows-you-to-figure-out) to give you perspective on the problem.
- Put on your scientist hat:
  - Question your assumptions and follow [the scientific method of debugging](https://medium.com/machine-words/scientific-debugging-part-1-8890b73b6c4c).
  - TLDR: observe the problem => form a hypothesis => test => repeat.
