Let's draw your first visualization.

For this example, we'll use the following JSON as the event data.
[block:code]
{
  "codes": [
    {
      "code": "var event = {\n  \"movieTitle\": \"The Matrix\",\n  \"movieLength\": 112,\n  \"lengthWatched\": 29,\n  \"views\": 1,\n  \"userId\": \"194337\",\n  \"userCountry\": \"Germany\",\n  \"deviceUsed\": \"Mobile\"\n}",
      "language": "json"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Step 1. HTML Wireframe"
}
[/block]
Read about [Including the SDK](doc:initializing-the-sdk) and follow the steps, you should end up with something like this:
[block:code]
{
  "codes": [
    {
      "code": "<html>\n  <head>\n    <script src=\"<APPLICATION_URL>/joola.min.js?APIToken=<READER_API_TOKEN>\"></script>\n    <script type=\"text/javascript\">\n      joola.on('ready', function(){\n        console.log('Joola is ready', joola.VERSION);\n      });\n    </script>\n  </head>\n  <body>\n  \t<div id=\"timeline\"></div>\n  </body>\n</html>",
      "language": "html"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Step 2. Design your query"
}
[/block]
We will drawing a Timeline showing the number of views over the last 30 days.
[block:code]
{
  "codes": [
    {
      "code": "var query = {\n\ttimeframe: 'last_30_days',\n  interval: 'day',\n  metrics: ['views'],\n  collection: 'JoolaFlix'\n};",
      "language": "javascript"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Step 3. Visualize"
}
[/block]
Lastly, we need to instruct the webpage to draw a timeline with the query results.
[block:code]
{
  "codes": [
    {
      "code": "<html>\n  <head>\n    <script src=\"<APPLICATION_URL>/joola.min.js?APIToken=<READER_API_TOKEN>\"></script>\n    <script type=\"text/javascript\">\n      joola.on('ready', function(){\n        console.log('Joola is ready', joola.VERSION);\n        var query = {\n          timeframe: 'last_30_days',\n          interval: 'day',\n          metrics: ['views'],\n          collection: 'JoolaFlix'\n        };\n        $('#timeline').Timeline({\n          caption: 'Movie views over last 30 days', \n          query: query\n        });\n      });\n    </script>\n  </head>\n  <body>\n    <div id=\"timeline\"></div>\n  </body>\n</html>",
      "language": "html"
    }
  ]
}
[/block]
You're all done, at this point, you should see something like this within your webpage.