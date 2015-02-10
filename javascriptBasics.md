# Javascript Basics #

### Starting off ###
- Using the javascript console on Google Chrome
- Download the basic.html file
- Open javascript console control+option+i
- Page source is control+option+u
- You can use the javascript console like a calculator 
- (Clearing the javascript console is control+l)
- You can also pull up what you last entered, using the UP button

### Variables ###
Like python, we can set integers to variable and treat them like integers. The difference in javascript is we have to explicitly state that they are variables, or "var." Arrays can also be variables, like var Data = [1,2,3,4,5];

### Functions ###
We can use functions to modify our variables, and there are primarily two types of functions:

Named Funcitons  
 - function myFunction(x) { return x * 2; } 
 - enter value into myFunction()
  
Unnamed Function 
- (function(x) { return x * 2; })(2);
- unnamed functions are aka IIFE (Immediately Invoked Function Expression)
- unnamed functions are most commonly used as part of a chain
