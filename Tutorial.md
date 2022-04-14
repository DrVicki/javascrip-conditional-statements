# Js Basics Conditionals 

### Problem Statement

you're hungry, you make a sandwich. If the traffic light is green, you press the gas pedal. If your rent is due, then you pay your rent. This breaks down into a lot of conditional choices:

    if hungry → make sandwich.
    else → don't make sandwich.
    if light is green → press gas pedal.
    else → press brake pedal.
    if it's the first of the month → pay rent.
    else → don't pay rent.

Writing code involves the same type of logic — we only want an action to happen if a certain condition is met. In the programming world, this is called **control flow** because, well, it helps control the flow of an application.

Before we dive into JavaScript's conditional structures, let's go over a few concepts to provide the syntactic underpinnings.

## Objectives

  - Explain what constitutes an expression in JavaScript
  - Organize code using block statements
  - Describe the difference between truthy and falsy values
  - Learn to use conditional statements
  - Explain What Constitutes an Expression in JavaScript


A JavaScript expression is a unit of code which returns a value. Primitive values are expressions because they resolve to a value:

```
9;
// => 9
```

```
('Hello, world!');
// => "Hello, world!"
```

```
false;
// => false
```
So are arithmetic and string operations. This code resolves to the number 64:

```
8 * 8;
// => 64
```
And this resolves to the string "Hello, world!":

```
'Hello, ' + 'world!';
// => "Hello, world!"
```
Ditto for comparison and assignment operations. This comparison resolves to the boolean true:

```
2 > 1;
// => true
```
Variable declarations are NOT expressions...

```
let answer;
```
...but variable assignments ARE, resolving to the assigned value (42, in this case):

```
answer = 42;
// => 42
```

Finally, references to variables are also expressions, resolving to the value contained in the variable:

```
const fullName = 'Ada Lovelace';

fullName;
// => "Ada Lovelace"
```

### Organize Code Using Block Statements

A block statement is a pair of curly braces (```{ }```) used to group JavaScript statements. It plays a role in conditional statements, loops, and functions.

```
{
    ('This line is a JavaScript statement nested inside a block statement!');

    // This is also a statement nested inside a block:
    5 * 5 - 5;

    // And so are these:
    const weCan = 'group multiple statements';

    const suchAs = 'these variable declarations';

    const insideA = 'block statement.';
}
// => 20
```

Block statements return the value of the last evaluated expression inside the curly braces. Remember, the variable declarations are not expressions, so the value of 5 * 5 - 5 is returned.

**Note**: The statement above implicitly returns 20 (the value returned by 5 * 5 - 5, when evaluated). Functions, which we will discuss in an upcoming lesson, also contain all of their code inside curly braces, but for functions, we need to explicitly use the word ```return``` to tell JavaScript what we want the output to be (if we want one, at all). Just remember the implicit ```return``` is something unique to block statements like the ones we use for if...else and loop statements.

### Describe the Difference Between Truthy and Falsy Values

Truthiness and falsiness indicate what happens when the value is converted into a boolean. If, upon conversion, the value becomes true, we say that it's a truthy value. If it becomes false, we say that it's falsy.

In JavaScript, the following values are falsy:

    false
    null
    undefined
    0
    NaN
    An empty string (, '', "")

Every other value is truthy.

To check whether a value is truthy or falsy in our browser's JS console, we can pass it to the global Boolean object, which converts the value into its boolean equivalent:

```
Boolean(false);
// => false

Boolean(null);
// => false

Boolean(undefined);
// => false

Boolean(0);
// => false

Boolean(NaN);
// => false

Boolean('');
// => false

Boolean(true);
// => true

Boolean(42);
// => true

Boolean('Hello, world!');
// => true

Boolean({ firstName: 'Brendan', lastName: 'Eich' });
// => true
```

**NOTE**: ```document.all``` is also falsy, but don't worry about it for now. (Or ever, really — it's an imperfect solution for legacy code compatibility.) Ready to put that killer new vocabulary to the test? Here we go!

### Learn to Use Conditional Statements

In JavaScript, we use three structures for implementing condition-based control flow: the if...else statement, switch statement, and ternary operator.

```if``` statement
if statements are the most common type of conditional, and they're pretty straightforward:

```
if (condition) {
    // Block of code
}
```
If the condition returns a truthy value, run the code inside the block:

```
const age = 30;

let isAdult;

if (age >= 18) {
    isAdult = true;
}
// => true

isAdult;
// => true
```

If the condition returns a falsy value, do nothing:

```
const age = 14;

let isAdult;

if (age >= 18) {
    isAdult = true;
}

isAdult;
// => undefined
else
```
If we want to run some code when the condition returns a falsy value, we can use an else clause:

```
const age = 14;

let isAdult;

if (age >= 18) {
    isAdult = true;
} else {
    isAdult = false;
}
// => false

isAdult;
// => false
```
### Nested Conditionals

If we have multiple overlapping conditions, we can employ nested conditional statements. 
    - For example, instead of just deciding whether the passed-in age meets the criteria for ```isAdult```, let's add in some other hallmarks of burgeoning adulthood (in American society, at least): ```canWork```, ```canEnlist```, and ```canDrink```. 
    - 16-year-olds can legally work; 18-year-olds can work, enlist, and are legal adults; and 21-year-olds can work, enlist, are legal adults, and can drink (at the federally set minimum age, although there can be state-to-state exceptions for these laws). Let's use these conditions in a nesting example:

```
const age = 17;

let isAdult, canWork, canEnlist, canDrink;

if (age >= 16) {
    canWork = true;

    if (age >= 18) {
        isAdult = true;
        canEnlist = true;

        if (age >= 21) {
            canDrink = true;
        }
    }
}

isAdult;
// => undefined

canWork;
// => true

canEnlist;
// => undefined

canDrink;
// => undefined
else if
```
Another way to represent multiple possible conditions is with else if clauses:

```
const age = 20;

let isAdult, canWork, canEnlist, canDrink;

if (age >= 21) {
    isAdult = true;
    canWork = true;
    canEnlist = true;
    canDrink = true;
} else if (age >= 18) {
    isAdult = true;
    canWork = true;
    canEnlist = true;
} else if (age >= 16) {
    canWork = true;
}
// => true

isAdult;
// => true

canWork;
// => true

canEnlist;
// => true

canDrink;
// => undefined
```
As soon as one of the conditions returns a truthy value, the attached code block runs and the conditional exits. If none of the conditions evaluate to a truthy value, then the ```else``` code block runs (or, in the absence of an ```else``` clause, the conditional simply exits). Note that, unlike the nested if statements above, at most one code block will run. In the absence of an ```else``` statement, it's possible none of the ```if``` conditions return a truthy value and no block is run. However, it's impossible for more than one block in a linked if...else if...else control flow to run.

```switch```
Running multiple blocks in the same control flow is one of the many talents of the ```switch``` statement. The general structure is as follows:

```
switch (expression) {
    case value1:
        // Statements
        break;
    case value2:
        // Statements
        break;
    default:
        // Statements
        break;
}
```
The JavaScript engine evaluates the expression and then compares the returned value against each of the case values using strict equality (```===```):

```
const hunger = 'famished';

let food;

switch (hunger) {
    case 'light':
        food = 'grapes';
        break;
    case 'moderate':
        food = 'sushi';
        break;
    case 'famished':
        food = 'lasagna';
        break;
}
// => "lasagna"

food;
// => "lasagna"
```

Generally, we use a ```switch``` statement if we need a conditional which hinges on a single value but requires a separate handler for each potential case. For example, the ```switch``` statement here doesn't require us to repeat the ```if``` (order === _____) line for each possibility:

```
const order = 'cheeseburger';

let ingredients;

switch (order) {
    case 'cheeseburger':
        ingredients = 'bun, burger, cheese, lettuce, tomato, onion';
        break;
    case 'hamburger':
        ingredients = 'bun, burger, lettuce, tomato, onion';
        break;
    case 'malted':
        ingredients = 'milk, ice cream, malted milk powder';
        break;
    default:
        console.log("Sorry, that's not on the menu right now.");
        break;
}
```
If we'd like to write out the same code with an ```if``` conditional, it will look like this:

```
const order = 'cheeseburger';

let ingredients;
if (order === 'cheeseburger') {
    ingredients = 'bun, burger, cheese, lettuce, tomato, onion';
} else if (order === 'hamburger') {
    ingredients = 'bun, burger, lettuce, tomato, onion';
} else if (order === 'malted') {
    ingredients = 'milk, ice cream, malted milk powder';
} else {
    console.log("Sorry, that's not on the menu right now.");
}
```
We can also assign the same set of statements to multiple cases. In the following example, if the age variable contains any number between 13 and 19, the ```isTeenager``` variable will be set to ```true```. If it contains anything other than a number between 13 and 19, none of our cases will hit, and it will end up at the default, which sets ```isTeenager``` to ```false```:

```
const age = 15;

let isTeenager;

switch (age) {
    case 13:
    case 14:
    case 15:
    case 16:
    case 17:
    case 18:
    case 19:
        isTeenager = true;
        break;
    default:
        isTeenager = false;
}
```
The ```default``` and ```break``` keywords are both optional in basic ```switch``` statements, but useful. In more complicated statements, they become necessary to ensure the correct flow.

```break```
In the previous example,```break``` is used to stop the ```switch``` statement from continuing to look at case statements. If instead, we wrote the following:

```
const age = 15;

let isTeenager;

switch (age) {
    case 13:
    case 14:
    case 15:
    case 16:
    case 17:
    case 18:
    case 19:
        isTeenager = true;
        console.log('case 19: ', isTeenager);
    default:
        isTeenager = false;
        console.log('default: ', isTeenager);
}
```
The ```switch``` statement would get to a match at case 15 and continue on through to case 19, setting ```isTeenager``` to ```true```. It would then get to ```default``` and set ```isTeenager``` to ```false```. You will often see ```switch``` statements where ```break``` is used in every case as a way to ensure there is no unexpected behavior from multiple cases executing.

However, sometimes we do want to potentially match multiple cases, and we will need to leave out ```break``` to do this. There's a neat little trick we can employ which allows us to use comparisons for case statements. Let's rewrite the above if...else chain as a more compact, less repetitious switch statement:

```
const age = 20;

let isAdult, canWork, canEnlist, canDrink;

switch (true) {
    case age >= 21:
        canDrink = true;
    case age >= 18:
        isAdult = true;
        canEnlist = true;
    case age >= 16:
        canWork = true;
}
// => true

isAdult;
// => true

canWork;
// => true

canEnlist;
// => true

canDrink;
// => undefined
```
We specified ```true``` as the value to switch on. All of our cases are comparisons, and if the comparison returns ```true``` its statements will be run. Because we did not include any break statements, once one case statement matches, all subsequent statements will execute.

With age set to 20 in the above example, the first case, ```age >= 21```, returns ```false``` and so the assignment of ```canDrink``` never happens. The engine then proceeds to the next case, ```age >= 18```, which returns ```true```, assigning the value true to ```isAdult``` and ```canEnlist```. Since it encounters no break statement, ```canWork``` is then set to ```true``` in the last case statement.

```default```

The ```default``` keyword specifies a set of statements to run after all of the switch statement's cases have been checked. The only time the default statements do not run is if the engine hits a break in one of the case statements.

```
const mood = 'quizzical';

let response;

switch (mood) {
    case 'happy':
        response = 'Heck yea; be happy!';
    case 'sad':
        response = "You're awesome; keep your head up!";
    default:
        response = "Sorry, I don't know how to respond to that mood.";
}
// => "Sorry, I don't know how to respond to that mood."

response;
// => "Sorry, I don't know how to respond to that mood."
It's typically safer to include break statements because it helps avoid bugs like this:

const mood = 'happy';

let response;

switch (mood) {
    case 'happy':
        response = 'Heck yea; be happy!';
    case 'sad':
        response = "You're awesome; keep your head up!";
    default:
        response = "Sorry, I don't know how to respond to that mood.";
}
// => "Sorry, I don't know how to respond to that mood."

response;
// => "Sorry, I don't know how to respond to that mood."
```

The 'happy' case matches and assigns the string 'Heck yea; be happy!' to response. However, since we didn't break after that assignment, the default case also runs and reassigns "Sorry, I don't know how to respond to that mood." to response. Whoops!

**Ternary operator**

The ternary operator, the final piece of the conditional puzzle, is a good way to represent an if...else statement in a single line of code:

condition ? expression1 : expression2;

If the condition returns a truthy value, run the code in expression1. If the condition returns a falsy value, run the code in expression2.

```
const age = 45;

let isAdult;

age >= 18 ? (isAdult = true) : (isAdult = false);
// => true

isAdult;
// => true
```
In the above example, we assign ```isAdult``` as ```true``` if the condition returns a truthy value and as false otherwise. We can simplify that a bit and assign the result of the ternary directly to a variable:

```
const age = 60;

const isAdult = age >= 18 ? true : false;

isAdult;
// => true
If it helps you visualize what's going on, you can wrap the condition, the expressions, or the entire ternary in parentheses:

const age = 17;

const isAdult = (age >= 18) ? true : false;

const canWork = (age >= 16) ? (1 === 1) : (1 !== 1);

const canEnlist = (isAdult ? true : false);

isAdult;
// => false

canWork;
// => true

canEnlist;
// => false
```

**Top Tip**: 

Be careful to not overuse the ternary operator. It's fine for slimming down a simple if...else, but be conscious of how easy your code is to understand for an outsider. Remember, you generally write code once, but it gets read (by yourself and others) far more than once. The ternary is often more difficult to quickly interpret than a regular old if...else, so make sure the reduction in code is worth any potential reduction in readability.

## Code Examples
There are tons of control flow structures in the Flatbook project code base, a project that emulates the basic functionality of Facebook.

if...else
When a guest tries to log in, check whether the provided email and password match an active account:

```
let errorMessage = '';
let loggedIn = false;

// *User enters a valid email and password and clicks the Login button*
const email = 'avi@flatbook.com';
const password = 'j4v45cr1pt 15 4w350m3';

// *The Flatbook app then checks whether the provided email and password are valid*
const accountFound = true;
const passwordMatches = false;

if (email === '') {
    errorMessage = 'Please provide an email.';
} else if (password === '') {
    errorMessage = 'Please provide a password.';
} else {
    if (accountFound) {
        if (passwordMatches) {
            loggedIn = true;
        } else {
            errorMessage = "Sorry, that password doesn't match our records.";
        }
    } else {
        errorMessage =
            'Sorry, no account matching the provided email address was found.';
    }
}
// => "Sorry, that password doesn't match our records."

loggedIn;
// => false

errorMessage;
// => "Sorry, that password doesn't match our records."
```
**Ternary operator**

When a user logs in, check whether it's their birthday. If it is, set a celebratory message to appear in a banner; else, set the message to an empty string:

```
const userBirthday = 'Dec 10';

const userFullName = 'Ada Lovelace';

let todaysDate = 'Dec 10';

const birthdayMessage =
    todaysDate === userBirthday ? `Happy birthday, ${userFullName}!` : '';

birthdayMessage;
// => "Happy birthday, Ada Lovelace!"
switch
```
Once the user logs in, set their permissions based on the account type:

```
const accountType = 'admin';

let permissionsLevel;
let canViewProfiles = false;
let canImpersonateUsers = false;

switch (accountType) {
    case 'guest':
        permissionsLevel = 0;
        break;
    case 'user':
        permissionsLevel = 10;
        canViewProfiles = true;
        break;
    case 'admin':
        permissionsLevel = 20;
        canViewProfiles = true;
        canImpersonateUsers = true;
        break;
}
// => true

permissionsLevel;
// => 20
```
## Conclusion

It's easy to imagine hundreds of other conditionals that go into the functioning of a large site like Flatbook. Conditional statements make the internet go round, so study up! The more comfortable you are with controlling the flow of your code with conditional statements, the more complex websites you will be able to build.

