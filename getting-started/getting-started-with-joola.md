[block:callout]
{
  "type": "info",
  "title": "",
  "body": "Joola is currently running in beta."
}
[/block]

[block:callout]
{
  "type": "success",
  "body": "This guide will walk you through getting started with Joola using cURL from your terminal."
}
[/block]
Joola is a data analytics framework for developers. With Joola you can track any event: visits, registrations, purchases, game play and more... events are pushed into Joola using a simple JSON format and managed within collections, which are logical containers for separating your data into topics. Joola's intuitive and powerful query API allows you to explore, analyze and visualize your data to gain insight into your performance. 

Joola's SDK includes beautiful and powerful visualizations for your data, you can use, add, modify and extend visualizations according to your needs, there are no limits. Canvases allow you to group visualizations into a fully working application with out-of-the-box interaction between the different visualizations.

Joola allows you to focus on developing your product and focus on what you do best while not needing to worry about developing a full scale data analytics solution.
[block:api-header]
{
  "type": "basic",
  "title": "Step 1 - setup a Joola application"
}
[/block]
If you haven't done so already, login to Joola and [create a new application](https://app.joo.la). Applications are used to keep your data separated and each application holds its set of security tokens for accessing and working with it.

Once you've created your application, you'll have access to its endpoints and security tokens, look under the Tokens section.
[block:api-header]
{
  "type": "basic",
  "title": "Step 2 - push an event"
}
[/block]
[Events](doc:events) are the pieces of information you wish to track and analyze. Events of the same topic are stored in [Collections](doc:event-collections), which are created on-the-fly as you send your first event. The example below creates a new Collection named `JoolaFlix`, but you can specify any name you wish.

We will be pushing a new `watch` event into the `JoolaFlix` collection. The event should be in JSON format and it looks like this example.

**The Event data** below is the JSON representation of the `watch` event.
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"movieTitle\": \"The Matrix\",\n  \"userId\": \"194337\",\n  \"userCountry\": \"Germany\",\n  \"deviceUsed\": \"Mobile\",\n  \"movieLength\": 112,\n  \"lengthWatched\": 29,\n  \"views\": 1\n}",
      "language": "json"
    }
  ]
}
[/block]
**Copy, modify and paste** the cURL statement below into a terminal window. Replace `<APPLICATION_URL>`, `<COLLECTION>` and `<WRITER_API_TOKEN>` with values specific to your application.
[block:code]
{
  "codes": [
    {
      "code": "curl -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n  \\\"movieTitle\\\": \\\"The Matrix\\\",\n  \\\"userId\\\": \\\"194337\\\",\n  \\\"userCountry\\\": \\\"Germany\\\",\n  \\\"deviceUsed\\\": \\\"Mobile\\\"\n  \\\"movieLength\\\": 112,\n  \\\"lengthWatched\\\": 29,\n  \\\"views\\\": 1\n}]\" https://<APPLICATION_URL>/insert/<COLLECTION>?APIToken=<WRITER_API_TOKEN>",
      "language": "shell"
    }
  ]
}
[/block]
A few notes on the above command:
- `-X` indicates that we wish to perform an HTTP POST operation.
- `-H` adds an `application/json` content-type header to the request.
- `--data-binary` includes the actual JSON payload of the event to push.

The **response** should look like:
[block:code]
{
  "codes": [
    {
      "code": "{\n    \"deleted\": 0,\n    \"errors\": 0,\n    \"inserted\": 1,\n    \"replaced\": 0,\n    \"skipped\": 0,\n    \"unchanged\": 0\n}",
      "language": "json"
    }
  ]
}
[/block]
**You're done**, your first event is pushed.

Let's review a few things that happened during this example:
- First, we sent a REST API request to your Joola application while specifying your application's specific URL, collection and security token.
- Since the collection did not exist before, Joola created it for you.
- Joola inserted the event into your collection and it is available for query and analysis.
- Lastly, you received confirmation on your insert.

Read more about pushing data into Joola using [cURL](doc:pushing-documents-to-joola), [Javascript](doc:pushing-documents-to-joola), [NodeJS](doc:pushing-documents-to-joola), [PHP](doc:pushing-documents-to-joola), [Python](doc:pushing-documents-to-joola) and more.

[block:callout]
{
  "type": "warning",
  "body": "Once you receive a response from the server that your event has been pushed, it may take a few seconds before it will appear in query results."
}
[/block]
Read more about [pushing events](doc:pushing-events).
[block:api-header]
{
  "type": "basic",
  "title": "Step 3 - analyze it!"
}
[/block]
Joola offers an intuitive and powerful query API, it's rich with possibilities, aggregations, filters and more, but for the purpose of this walk-through we'll focus on a single aggregation `SUM`, which does exactly what it sounds like it does, it sums a value of pushed events.

For this example, we'll sum the number of `views` of a `watch` event within the `JoolaFlix` collection.

**Copy, modify and paste** the cURL statement below into a terminal window. Replace `<APPLICATION_URL>`, `<COLLECTION>` and `<READER_API_TOKEN>` with values specific to your application.
[block:code]
{
  "codes": [
    {
      "code": "curl -X POST -H \"Content-Type: application/json\" --data-binary \"{ \n    \\\"metrics\\\": [\n      {\n        \\\"key\\\": \\\"views\\\",\n        \\\"aggregation\\\": \\\"sum\\\"\n      }\n    ],\n    \\\"collection\\\": \\\"JoolaFlix\\\"\n}\" https://<APPLICATION_URL>/insert/<COLLECTION>?APIToken=<READER_API_TOKEN>",
      "language": "shell"
    }
  ]
}
[/block]
The **response** will look like this:
[block:code]
{
  "codes": [
    {
      "code": "{\n\t\"views\": 1 \n}",
      "language": "json"
    }
  ]
}
[/block]
Since we've inserted only one event, the result will show 1. If you keep pushing events from the previous step, you'll see this counter increase accordingly.

Read more about [querying data]() and using [timelines](doc:timeline), [tables](doc:table), [pie charts](doc:pie), [metric boxes](doc:metricbox) and more to show sums, counts, averages and more analysis.
[block:api-header]
{
  "type": "basic",
  "title": "Step 4 - visualize it!"
}
[/block]
Visualization is based on queries, let's take the query from the previous step and draw a metric box showing the `SUM` of `views`.

Create a simple HTML page and **Copy, modify and paste** the statement below. Replace `<APPLICATION_URL>`, `<COLLECTION>` and `<WRITER_API_TOKEN>` with values specific to your application. 
[block:code]
{
  "codes": [
    {
      "code": "<html>\n  <body>\n    <div id=\"example\"></div>\n    <script src=\"<APPLICATION_URL>/joola.js?APIToken=<READER_API_TOKEN>\"></script>\n    <script language=\"javascript\">\n      joola.on('ready', function(){\n        $('#example').Metric({\n          caption: 'Movie views',\n          query: {\n            metrics: ['views'],\n            collection: 'JoolaFlix'\n          }\n        });\n      });\n    </script>\n  </body>\n</html>",
      "language": "html"
    }
  ]
}
[/block]
**You're done**, your browser will display a simple Metric Box visualization.

Let's review a few things that happened during this example:
- First, we created a simple, stand-alone HTML page.
- We included Joola's SDK and created a placeholder div named `example`.
- We waited for Joola to become ready.
- Once ready, we instructed it to draw a Metric Box within the `example` div that shows the total sum of views.
[block:api-header]
{
  "type": "basic",
  "title": "Step 5 - build complete data analytics application"
}
[/block]
Now it's time to start building your data analytics application.

Read about Joola's [visualizations](doc:visualization-overview), [canvases](doc:canvases) and [data modeling](doc:data-modeling).

If you need a hand, just [give us a shout](mailto:support@joo.la).