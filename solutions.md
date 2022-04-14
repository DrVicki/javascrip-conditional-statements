What does the following expression return?

    4 > 1;

    Solution:
    true
    4 is greater than 1, so the expression evaluates to true. 4 and 1 are referred to as the operands and > is the operator.

What does the following expression return?

    "chatty" === "chatty";

    Solution:
    true
    The "chatty" strings both have the same length and the same elements in the same order, so the === operator returns true.


What does the following expression return?

    3 <= 300

    Solution:
    true
    The number 3 is less than or equal to 300.


Print the string "I just ate a lot" to the console.
  
    Solution:
    console.log("I just ate a lot");


if statements will execute the code in the block if the boolean condition is true. What does the following expression print to the console?

    if (5 === 5) {
      console.log("This code is executed");
    }

    Solution:
    "This code is executed"
    The boolean condition 5 === 5 evaluates to true, so the code in the block is executed. The code block is delimited by {}.

  
What does the following expression print to the console?

    if (5 > 10) {
      console.log("Not so sure about this");
    }

    Solution:
    Nothing is printed to the console because the boolean condition is false. When the boolean condition is false, the code in the code block is not executed.


What does the following expression print to the console?

    if (5 > 10) {
      console.log("Not so sure about this");
    } else {
      console.log("walking dead");
    }

    Solution:
    "walking dead"
    When the boolean condition evaluates to false (5 > 10), the code block associated with the if keyword is not executed and the code block associated with the else keyword is executed.


What does the following expression print to the console?

    if ("candy" === 8) {
      console.log("do something with your life");
    } else if ("blah" === "blah") {
      console.log("just chill, have fun");
    } else {
      console.log("people are strange");
    }

    Solution:
    "just chill, have fun"
    is printed to the console as the boolean condition associated with the else if clause is true.

  
What does the following expression print to the console?

    if (5) { console.log("I like peanuts"); }

    Solution:
    "I like peanuts" is printed to the console. 5 does not equal true or false, but it is considered "truthy" in a boolean context. Type Boolean(5) in the console to see if the number 5 is considered truthy or falsey. In JavaScript, undefined, NaN, null, 0, "", and the keyword false are all false in a boolean context. All other values are truthy.



What does the following expression print to the console?

    if ("") {
      console.log("program more");
    } else if ("cool") {
      console.log("party hard!");
    } else {
      console.log("blah");
    }

    Solution:
    "party hard!"
    "party hard!" is printed to the console because "cool" is truthy. "program more" is not printed to the console because the empty string is falsey.

  
What does the following expression return?

    !false

    Solution:
    true
    The ! operator returns the opposite of the boolean value it is prepended to.


What does the following expression print to the console?

    if (!undefined) console.log("This syntax is weird…");

    Solution:
    "This syntax is weird..."
    !undefined is true in a boolean context, so the code block associated with the if statement is executed. The code block is not delimited with {}    
    because the curly brackets are optional when the code block is on the same line as the if statement. For multi-line code blocks, the curly brackets 
    are required.
