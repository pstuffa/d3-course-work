# D3 Fundamentals - Day Two #

Today's goal will be to learn how a this Bostock example works, and how to make your own using one of these four Bostock examples.

--- 
Next up..



Transitions 
- making things happen smoothly


Let's go back to index.html, and try binding data to our cicle using these methods.

```javascript
// Define your data 
var dataset = [10]
// Select the cirlce, and update it with data
d3.select("svg").selectAll("circle")
.data(dataset);
```
Select the circle and look at the data property to confirm it's updated. That's the update method. Simply select your objects and use the data() function to update them with data. To note, you only want to do this when there's a 1 to 1 relationship between your objects and your data.

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
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return Math.random()*400; } )
.attr("cy", function(d,i) { return Math.random()*400; } )
.attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
    })
.style("fill-opacity", .7)
.style("stroke-width",".2em")
.style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
    });    
```
- What's this function(d)?
- What's cx and cy?
- What's r?


---


Events
- making things happen
- 

---


The Inverted Coordinate Plane
- *Note the difficulty in bar graphs because of the inverted shapes



---

Axes 
- Lines
- Transform functions 



---
Pulling in Data from Files
- Go over the data function



Bostock Example 
- http://bl.ocks.org/mbostock/3887118
