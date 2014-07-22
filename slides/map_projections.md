###Projections
#####try it: http://bit.ly/1kaRvzw



<pre>
svg.select(".counties")
    .selectAll("path")
    .data(topojson.feature(us, us.objects.counties).features)
    .enter().append("path")
    .attr("d",path)
    .attr("fill", function(d) {return quantize(topic_value_handler(data,d.id,selected_topic))})
</pre>

Note:
D3 has may geographic [projections](https://github.com/mbostock/d3/wiki/Geo-Projections). I am using the default, which is d3.geo.albersUSA
