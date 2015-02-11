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

Let's make a few variables:

```
make a variable called numerator, equal to 99
make a variable called denominator, equal to 100
make a variable called percent, equal to the numerator divided by the denominator
make a dataset called dataset, equal to five random numbers 

```




### Functions ###
We can use functions to modify our variables, and there are primarily two types of functions:

#### Named Funcitons ####
 - function myFunction(x) { return x * 2; } 
 - Enter value into myFunction()
  
#### Unnamed Function ####
- (function(x) { return x * 2; })(2);
- Unnamed functions are aka IIFE (Immediately Invoked Function Expression)
- Unnamed functions are most commonly used as part of a chain, so something like:
```
var data = [1,2,3,4,5]

data.map( function(x) { return x * 2;} );
```
*This will be very important in D3, as we will often make functions on the fly. The difference in D3 is that we won't necessarily nest the function within a map() function.*


You can also filter in functions
```
var data = [1,2,3,4,5]

data.map( function(x) { return x * 2 == 2;} );


or 


var data = [1,2,3,4,5]

data.map( function(x) { if(x * 2 == 2) {return x;}} );
```
*Notice the difference in what those two return - the latter is what is more commonly used in D3*


Let's make a few functions: 
```



```



