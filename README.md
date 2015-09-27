## D3 Based Real Time Chart

The real time chart is a resuable Javascript component that accepts real time data. The chart's time domain is moving with the passage of time, which means that any data placed in the chart eventually will age out and leave the chart. In addition to the main chart, the component also manages a "focus" window with a viewport (d3.brush) that can moved and sized to view an arbitrary portion of the time series data. 

The component adheres to the pattern described in [Towards Reusable Chart](http://bost.ocks.org/mike/chart/). 

The following options are currently supported:
- **width** and **height** in pixels (Number)
- **border** (Boolean)
- **title**, **xTitle**, **yTitle** (String)
- **barWidth** in pixels (Number)

Future options will include:
– Scale domain of real time data (currently a domain of [0, 100] is assumed for the y scale)
- Use of SVG rects, circles, paths etc. to represent data (in addition to bars)

Use the component like so:

`
// create the real time chart
var chart = realTimeChart()
    .title("Chart Title")
    .yTitle("Y Scale")
    .xTitle("X Scale")
    .border(true)
    .width(600)
    .height(290)
    .barWidth(1)
    .initialData(data);

// invoke the chart
var chartDiv = d3.select("#viewDiv").append("div")
    .attr("id", "chartDiv")
    .call(chart)

// create new data item and inject into chart
var now = new Date();
var obj = {
  value: 50
  time: now,
  color: "red",
  ts: now.getTime(),
  interval: timeout
}

// send the datum to the chart
chart.datum(obj);
`
