Visualize metrics and dimensions in a table.
[block:code]
{
  "codes": [
    {
      "code": "joola.events.on('ready', function() {\n  $('#example').Table({\n    limit: 5,\n    query: {\n      timeframe: 'last_30_days', \n      interval: 'day', \n      dimensions: ['userCountry', 'movieTitle'],\n      metrics: ['views'],\n      collection: 'JoolaFlix',\n      realtime: true\n    }\n  });\n});",
      "language": "javascript"
    }
  ]
}
[/block]
#EXAMPLE

The example below renders a Table for the movie views by the user's country and the movie title at JoolaFlix our fictitious online movie rental business.
[block:html]
{
  "html": "<div id=\"table-example\">\n  <div class=\"switchbox\">\n  \t<div class=\"switch\"></div>\n  \t<div class=\"switch\" id=\"switch2\"></div>\n\t</div>\n</div>"
}
[/block]
See more examples on our [CodePen Table collection](http://codepen.io/collection/izcEI/)

#PROPERTIES

|  PROPERTY | TYPE  | DEFAULT  | DESCRIPTION |
|---|---|---|---|
| `limit` | Integer |  | **Optional**. Limit the number of results shown on the table.
| `query` | Object |   | **Required**. The [query object](/v1.0/docs/the-query-object) |

#EVENTS

|  EVENT | DESCRIPTION |
|---|---|
| `table.init.start` | Fired when the Table starts loading |
| `table.init.finish` | Fired when the Table finishes loading |

#HTML TEMPLATE