###D3 scales 
#####(choropleth color gradation)
####try it: http://bit.ly/1r3wgOx
```javascript
var linear1 = d3.scale.linear()
                  .domain([0,1])
                  .range([10,20])
```

```javascript
max = 10
var linear2 = d3.scale.linear()
                  .domain([0,max])
                  .interpolate(d3.interpolateRgb)
                  .range(['#fee8c8','#e34a33'])
```

```javascript
max = 9
var quantize = d3.scale.quantize()
                  .domain([0,max])
                  .range(["rgb(247,251,255)"
                    ,"rgb(222,235,247)"
                    ,"rgb(198,219,239)"
                    ,"rgb(158,202,225)"
                    ,"rgb(107,174,214)"
                    ,"rgb(66,146,198)"
                    ,"rgb(33,113,181)"
                    ,"rgb(8,81,156)"
                    ,"rgb(8,48,107)"]);
```
Note:

Scales are functions.  

When the connection between domain/range is not obvious, the explicit use of the .interpolate() parameter creates a parameter based on the value from the domain and applies the maping according to the given scale. The use of interpolateRgb is called a "factory" that defines the color space between two given values. **this is awesome - it taps d3.rgb() to convert the given values.    

primary: red, blue, and yellow.   
hex: red, green, and blue. - green contains yellow.   
Hex numbers use 16 digits:  
0 1 2 3 4 5 6 7 8 9 A B C D E F  

F	15 X 16^0 =	15
F	15 X 16^1 =	240
HEX FF =	255

Zero, "0", is the smallest representations of a color. It's almost the total absence of color. F is 15 times the intensity of the color of 0. Combinations of these digits create different shades of a particular color. Double Zero, "00," is equal to zero hue. FF is equal to a pure color.

http://colorbrewer2.org/

d3.rgb(255,0,0)  
d3.rgb("red")  
d3.rgb('#ff0000')  
  
valid colors: http://www.w3.org/TR/SVG/types.html#ColorKeywords

show viz on ds-6 and gnip.github  
*  explain the color variation   
*  explain the project:   
    1.  grabed a small dataset of geotagged tweets
    1.  each county is colored by the percent of geotagged tweets containing users of a specific category      
    2.  categorizing tweets by topic (potentially majic, but we sell Klout data to do this now)  
    3.  the domain varied by topic so hardcoding the domain caused problems

var s = d3.scale.linear.domain([0,100]).range([10,20])

d3.selectAll("rect").data(data)
  .enter().append("svg:rect")
    .attr("height", s)

If that use of s seems magic, equivalents would be

.attr("height", function(n) { return s(n); })
 
.attr("height", function(n) { return 10 + 10 * (n/100) });


DEMO scales
