# D3 Fundamentals - Day Two #

Today's goal will be to learn about Transitions, Events, Margins/Axes, then how Bostock example works, and how to make your own using one of these four Bostock examples.

--- 


### Transitions ###
Transitions are functions within the D3 library that allow for seamless transitions between changes in your D3. They're a great way to add more interaction to your visualization. (Transitions are often called in D3 ["tweening"](http://bl.ocks.org/mbostock/1020902))

Let's go back to index.html, and try adding some transitions while we make changes

Let's run the first version
```javascript

var dataset = [10,20,30,40];

var svg = d3.select("body").append("svg")
.attr("width",700)
.attr("height", 700);

var circles = d3.select("svg").selectAll("circle");

circles.data(dataset)
.enter().append("circle")
.transition()
.duration(500)
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return d*10; } )
.attr("cy", function(d,i) { return d*10; } )
.attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    })
.style("fill-opacity", .7)
.style("stroke-width",".2em")
.style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    }); 
```

Now let's add a trasitions to the update:

```javascript

var dataset = [20,30,10,40];

circles.data(dataset)
.transition()
.duration(500)
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return d*10; } )
.attr("cy", function(d,i) { return d*10; } )
.attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    })
.style("fill-opacity", .7)
.style("stroke-width",".2em")
.style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    }); 
```

See what happened?










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
