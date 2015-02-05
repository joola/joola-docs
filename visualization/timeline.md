Visualize a metric on a linechart according to a dimension (Usually `timestamp`).
[block:code]
{
  "codes": [
    {
      "code": "joola.events.on('ready', function() {\n  $('#example').Timeline({\n    query: {\n      timeframe: 'last_30_days', \n      interval: 'day', \n      dimensions: ['timestamp'],\n      metrics: ['views'],\n      collection: 'JoolaFlix',\n      realtime: true\n    }\n  });\n});",
      "language": "javascript"
    }
  ]
}
[/block]
#EXAMPLE

The example below renders a 7-day timeline, day by day for the movie views at JoolaFlix our fictitious online movie rental business.
[block:html]
{
  "html": "<div id=\"timeline-example\">\n  <div class=\"switchbox\">\n  \t<div class=\"switch\"></div>\n  \t<div class=\"switch\" id=\"switch2\"></div>\n\t</div>\n</div>"
}
[/block]
See more examples in our [CodePen collection](http://codepen.io/collection/cnsEC/)

#PROPERTIES

|  PROPERTY | TYPE  | DEFAULT  | DESCRIPTION |
|---|---|---|---|
| `caption` | String | | **Optional**. A caption for the chart |
| `chart` | Object |  | **Optional**. A Highcharts chart object |
| `legend` | Boolean | true  | **Optional**. Display a legend for the chart |
| `query` | Object |   | **Required**. The [query object](/v1.0/docs/the-query-object) |
| `pickers` | Object |  | **Optional**. Holds reference to pickers |
| `pickers.main` | Object | | Holds reference to the main picker |
| `pickers.main.enabled` | Boolean | false | **Optional**. Show main metric picker |
| `pickers.secondary` | Object | | Holds reference to the secondary picker |
| `pickers.secondary.enabled` | Boolean | false | **Optional**. Show secondary metric picker |

#EVENTS

|  EVENT | DESCRIPTION |
|---|---|
| `timeline.init.start` | Fired when the Timeline starts loading |
| `timeline.init.finish` | Fired when the Timeline finishes loading |
[block:code]
{
  "codes": [
    {
      "code": "joola.events.on('timeline.init.finish', function() {\n\tconsole.log('Timeline finished loading'); \n}\n                \n//OR\n                \n$('#example').Timeline({\n  query: {\n  \t... \n  }\n}, function(err, ref) {\n  ref.on('timeline.init.finish', function() {\n    console.log('Timeline finished loading'); \n  });\n});",
      "language": "javascript"
    }
  ]
}
[/block]
#DEFAULT HTML TEMPLATE
[block:code]
{
  "codes": [
    {
      "code": "<div class=\"jio timeline caption\"></div>\n\t<div class=\"jio timeline chartwrapper\">\n\t<div class=\"jio timeline controls\">\n\t\t<div class=\"jio timeline primary-metric-picker\"></div>\n  \t<div class=\"jio timeline secondary-metric-picker\"></div>\n  </div>\n  <div class=\"jio timeline thechart\" style=\"width:100%;margin:0 auto\"></div>\n</div> ",
      "language": "html"
    }
  ]
}
[/block]