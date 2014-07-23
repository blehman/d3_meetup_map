###D3 geo data binding
####(choropleth map outline)
#####compare: http://bit.ly/1kaRvzw vs http://bit.ly/1lsjjKo

```javascript
svg.append("path")
  .datum(topojson.mesh(us))
  .attr("d", path);

```
vs
```javascript
svg.select(".counties")
    .selectAll("path")
    .data(topojson.feature(us, us.objects.counties).features)
    .enter().append("path")
    .attr("d",path)
```

*  use console:

```javascript
d3.json("data/counties.json", function(error, us) {  
    console.log("TOPO obj:", topojson.mesh(us))  
    }); 

d3.json("data/counties.json", function(error, us) {
    console.log("TOPO array:", topojson.feature(us, us.objects.counties).features)
    });
```


Note:

d3.json("data/counties.json", function(error, us) {
    console.log("TOPO obj:", topojson.mesh(us))  
    });  

d3.json("data/counties.json", function(error, us) {console.log("TOPO array:", topojson.feature(us, us.objects.counties).features)});

D3 has may geographic [projections](https://github.com/mbostock/d3/wiki/Geo-Projections). I am using the default, which is d3.geo.albersUSA

The counties.json file that I've used has been converted to TopoJSON and projected to Albers USA. See http://bost.ocks.org/mike/bubble-map/ for the low down on how to make this conversion simple. 


