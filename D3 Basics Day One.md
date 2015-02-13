# D3 Fundamentals #

The goal for this lesson will be for you to understand how goal.html works. Let's take a look at the code and see what we understand already.

```javascript
<!DOCTYPE html>
<html>
  <head>
  <title>D3 Basics</title>
    <script src="http://d3js.org/d3.v3.min.js" charset="utf-8"></script>
  </head>

  <body>

    <script>

    var dataset = [10, 5, 23, 12, 50, 2, 13, 8],
        colorScale = d3.scale.category20c();

    var svg = d3.select("body").append("svg")
        .attr("width", 600)
        .attr("height", 600)

    svg.selectAll("rect")
      .data(dataset)
       .enter().append("rect")
      .attr("x", function(d,i) { return i * 40; })
      .attr("y", 10)
      .attr("width", 30)
      .attr("height", function(d) { return d * 10; })
      .style("fill", function(d,i) { return colorScale(i); });

    </script>
  </body>
</html>
```

- src="http://d3js.org/d3.v3.min.js" charset="utf-8"
- d3.scale, d3.select("body")?
- function(d), function(d,i)?
- rect, x, y?
- selectAll(), data(), enter(), append()?
- svg a variable?
- Coordinate space inverted?

**Remember D3 is a Javascript framework, so there are all these functions specific to D3**

*For the full list of functions and uses, go [here](https://github.com/mbostock/d3/wiki/API-Reference)* 

---

### Selections ###
D3 is **data-driven-documentation**, and what that means is we are binding data to DOM elements. To do that, we need to select DOM elements, and specify what we want to bind.

There are two key functions for selections in D3:
- select() - grabs one element (the first)
- selectAll() - grabs all matching elements

![DOM Tree Example](http://cdn0.mos.techradar.futurecdn.net/Review%20images/Linux%20Format/Issue%20118/DOM%20tree%20inline2-420-90.jpg "DOM Tree Example")


D3 selections are based on CSS selectors, so you can use any of the following to select your d3 elements:
```
#grabthis       ==   <anything id="grabthis">
.grabthis       ==   <anything class="grabthis">
grabthis        ==   <grabthis>
grab = this     ==   <anything grab="this">
grab this       ==   <grab><this></grab>
```
*For the most part, you don't want to write code that requires you to select things in 5 different ways. Most go with the simple "grabthis" and ".grabthis" approach, but it's nice to know you have options.*

---

Let's go back to our basic.html example and try to do the following:
```
Grab the first p tag
Grab the third p tag
Grab all the p tags
```
*For each of these examples, look at what you got in the javascript console and figure out why it's the right selection.*


For more on how selections work, check out Mike Bostock's (awesome post about it)[http://bost.ocks.org/mike/selection/], which I will admit, is a little intimidating.

---

Now that we can select things, let's start doing things! Try out some of the following on basic.html:
```javascript
d3.select("p").style("color","red");
d3.selectAll("p").style("font-size","20px");
d3.select("#da_id").style("background-color","green");
```

While that's fun, what we really want to learn is how to bind **data**. Type in the following and check out the result:
```javascript
d3.select("p");
```
Now enter this and see what changed:
```javascript
d3.select("p").data([10])
```
See that __data__ property? That's your data!

Before we start going more into selections, let's talk about SVGs.

---

### SVGs ###
For every D3 visualization, you will need a SVG, your canvas. SVGs are html objects, so can make them in html simply by writing:
```javascript
<svg width="700" height="700"></svg>
```

Inside that SVG is where you place your objects, which must be SVG objects. Here's an example you can add to your basic.html file:
```javascript
<svg width="700" height="700">
  <circle cx="100" cy="100" r="50" fill="red">
</svg>
```

Add this code to your basic.html, and reload the page.

Now, with your knowledge of select(), try the following:
```
Make the circle green
Make the circle HUGE
Make the circle tiny
Make the circle disappear!
```

*[Go here](http://www.w3schools.com/svg/default.asp) to see all the SVG objects and what attributes they require. This is important, as often, issues with creating different SVG objects happens when one uses the wrong attributes, such as setting x and y coordinates for a cirlce, which require cx and cy coordinates.*

---

### Enter, Update, and Exit ###

![D3 Venn](https://s3.amazonaws.com/assets-paperboy/adunkman/techtime-understanding-d3-selection-operations-venn.png "D3 Venn")

- Enter : used to add / create objects with bounded data
- Update : used to update existing objects with bounded data 
- Exit : used to update existing objects and remove objects when there is no element to match to data
*If you wanted to remove all objects, you use the .remove() function*


Let's go back to basic.html, and try binding data to our cicle using these methods.

```javascript
// Define your data 
var dataset = [10]
// Select the cirlce, and update it with data
d3.select("svg").selectAll("circle")
.data(dataset);
```
Select the circle and look at the data property to confirm it's updated.

---

Now, let's use a larger dataset, and try the enter method.

```javascript
// Define new dataset
var dataset = [10,20,30]
//Select the circle, use the enter() function and append circles to match the data
d3.select("svg").selectAll("circle")
.data(dataset)
.enter().append("circle");
```
- Where are the circles?

```javascript
d3.selectAll("circle")
.attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
    })
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return (i+1)*100; } )
.attr("cy", function(d,i) { return (i+1)*100; } );
```
- What's this function(d)?
- What's cx and cy?
- What's r?

---

## Review ## 

Now that we got a good sense of selections, SVGs and enter(), let's go back to our first visualization and answer a few questions:

```javascript
<!DOCTYPE html>
<html>
  <head>
  <title>D3 Basics</title>
    <script src="http://d3js.org/d3.v3.min.js" charset="utf-8"></script>
  </head>

  <body>

    <script>

    var dataset = [10, 5, 23, 12, 50, 2, 13, 8],
        colorScale = d3.scale.category20c();

    var svg = d3.select("body").append("svg")
        .attr("width", 600)
        .attr("height", 600)

    svg.selectAll("rect")
      .data(dataset)
       .enter().append("rect")
      .attr("x", function(d,i) { return i * 40; })
      .attr("y", 10)
      .attr("width", 30)
      .attr("height", function(d) { return d * 10; })
      .style("fill", function(d,i) { return colorScale(i); });

    </script>
  </body>
</html>
```
- Why is SVG a variable?
- Why do we say selectAll before the rectangles exist?
- What's that colorScale thing?


--- 

# Day One Challenge #

1. Make an SVG with five circles, all with different colors.
2. 

