###D3 scales 
#####(choropleth color gradation)
###http://bit.ly/WxMDK2

<pre>
var scale1 = d3.scale.linear()
                  .domain([0,1])
                  .range([300,320])
</pre>

<pre>
max=10
var scale2 = d3.scale.linear()
                  .domain([0,max])
                  .interpolate(d3.interpolateRgb)
                  .range(['#fee8c8','#e34a33'])
</pre>
Note:
show viz: ds-6 and gnip.github


Explain the project: 
2.) each county is colored by the percent of geotagged tweets
1.) categorizing tweets by topic (potentially majic, but we sell Klout data to do this now)
2.) the range varied by topic so hardcoding the domain caused problems
