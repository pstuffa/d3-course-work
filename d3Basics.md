# D3 Fundamentals #

The goal for this lesson will be for you to understand how goal.html works. Let's take a look at the code and see what we do understand aready.

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

**Remember D3 is a Javascript framework, so there are all these functions specific to D3**

*For the full list of functions and uses, go [here](https://github.com/mbostock/d3/wiki/API-Reference)* 



### SVGs ###
For every D3 visualization, you will need a SVG, your canvas. SVGs are html objects, so can make them in html simply by writing:
```
<svg width="200" height="200"></svg>
```

Inside that SVG is where you place your objects, which must be SVG objects. Here's an example you can add to your basic.html file:
```
<svg width="200" height="200">
  <circle cx="100" cy="100" r="50" fill="red">
</svg>
```

*[Go here](http://www.w3schools.com/svg/default.asp) to see all the SVG objects and what attributes they require. This is important, as often, issues with creating different SVG objects happen when one uses the wrong attributes, such as setting x and y coordinates for a cirlce, which require cx and cy coordinates.*



