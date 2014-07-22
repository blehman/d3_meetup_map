###Projections
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
Note:
D3 has may geographic [projections](https://github.com/mbostock/d3/wiki/Geo-Projections). I am using the default, which is d3.geo.albersUSA
