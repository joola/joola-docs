Visualize a metric on a Pie chart according to a dimension.
[block:code]
{
  "codes": [
    {
      "code": "joola.events.on('ready', function() {\n  $('#example').Pie({\n    limit: 5,\n    query: {\n      timeframe: 'last_30_days', \n      interval: 'day', \n      dimensions: ['userCountry'],\n      metrics: ['views'],\n      collection: 'JoolaFlix',\n      realtime: true\n    }\n  });\n});",
      "language": "javascript"
    }
  ]
}
[/block]
#EXAMPLE

The example below renders a Pie chart for the movie views by the user's country at JoolaFlix our fictitious online movie rental business.
[block:html]
{
  "html": "<div id=\"pie-example\">\n  <div class=\"switchbox\">\n  \t<div class=\"switch\"></div>\n  \t<div class=\"switch\" id=\"switch2\"></div>\n\t</div>\n</div>"
}
[/block]
See more examples on our [Pie CodePen collection](http://codepen.io/collection/HueLE/)

#PROPERTIES

|  PROPERTY | TYPE  | DEFAULT  | DESCRIPTION |
|---|---|---|---|
| `caption` | String | | **Optional**. A caption for the chart |
| `chart` | Object |  | **Optional**. A Highcharts chart object |
| `legend` | Boolean | true  | **Optional**. Display a legend for the chart |
| `query` | Object |   | **Required**. The [query object](/v1.0/docs/the-query-object) |

#EVENTS

|  EVENT | DESCRIPTION |
|---|---|
| `pie.init.start` | Fired when the Pie starts loading |
| `pie.init.finish` | Fired when the Pie finishes loading |

#HTML TEMPLATE
[block:code]
{
  "codes": [
    {
      "code": "<div class=\"jio-pie-caption\"></div>\n<div class=\"jio-pie-chart\"></div>",
      "language": "html"
    }
  ]
}
[/block]