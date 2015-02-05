Visualize a single Metric
[block:code]
{
  "codes": [
    {
      "code": "joola.events.on('ready', function() {\n  $('#example').Metric({\n    caption: 'Movie views',\n    query: {\n      timeframe: 'last_30_days', \n      interval: 'day', \n      metrics: ['views'],\n      collection: 'JoolaFlix',\n      realtime: true\n    }\n  });\n});",
      "language": "javascript"
    }
  ]
}
[/block]
#EXAMPLE

The example below renders a Metric at JoolaFlix our fictitious online movie rental business.
[block:html]
{
  "html": "<div id=\"metric-example\">\n  <div class=\"switchbox\">\n  \t<div class=\"switch\"></div>\n  \t<div class=\"switch\" id=\"switch2\"></div>\n\t</div>\n</div>"
}
[/block]
See more examples on our [CodePen Metric collection](http://codepen.io/collection/izcEI/)

#PROPERTIES

|  PROPERTY | TYPE  | DEFAULT  | DESCRIPTION |
|---|---|---|---|
| `caption` | String |  | **Optional**. Set a caption for the Metric
| `query` | Object |   | **Required**. The [query object](/v1.0/docs/the-query-object) |

#EVENTS

|  EVENT | DESCRIPTION |
|---|---|
| `metric.init.start` | Fired when the Metric starts loading |
| `metric.init.finish` | Fired when the Metric finishes loading |

#HTML TEMPLATE
[block:code]
{
  "codes": [
    {
      "code": "<div class=\"jio metricbox wrapper\">\n\t<div class=\"jio metricbox caption\"></div>\n\t<div class=\"jio metricbox value\"></div>\n</div>",
      "language": "html"
    }
  ]
}
[/block]