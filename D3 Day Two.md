# D3 Fundamentals - Day Two #

Today's goal will be to learn about Transitions, Events, Margins/Axes, then how Bostock example works, and how to make your own using one of these four Bostock examples.

--- 


### Transitions ###
Transitions are functions within the D3 library that allow for seamless transitions between changes in your D3. They're a great way to add more interaction to your visualization. 

Let's go back to index.html, and try adding some transitions while we make changes
```javascript
var dataset = [10,20,30,40];

var svg = d3.select("body").append("svg")
.attr("width",700)
.attr("height", 700);

var circles = svg.selectAll("circle");

circles.data(dataset)
.enter().append("circle")
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return (i + 1) *100; } )
.attr("cy", function(d,i) { return (i + 1) *100; } )
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

Now let's add a trasition to the update:
```javascript
var dataset = [10,20,30,40];

var svg = d3.select("body").append("svg")
.attr("width",700)
.attr("height", 700);

var circles = svg.selectAll("circle");

circles.data(dataset)
.enter().append("circle")
.transition()
.duration(2000)
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return (i + 1) *100; } )
.attr("cy", function(d,i) { return (i + 1) *100; } )
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

Let's play with some of the transition parameters to change our transitions:
- ease()
- delay()
- duration()

```javascript
var newdata = [30,10,20,40];

d3.select("svg").selectAll("circle")
.data(newdata)
.transition()
.duration(2000)
.ease("elastic")
.delay(200)
.attr("r", function(d) { return d*2; })
.attr("cx", function(d,i) { return (i + 1) *100; } )
.attr("cy", function(d,i) { return (i + 1) *100; } )
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

- ease() // applies various time value ranges
- delay() // add a delay 
- duration() // say how long you want it to be
<br />
<br />
<br />
<br />
For more transition parameters, [check out the API](https://github.com/mbostock/d3/wiki/API-Reference#d3-core).






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
