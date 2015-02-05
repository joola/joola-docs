The following example shows how you can use Joola to collect and visualize website visitor data. [Jump to result](#result) 
[block:api-header]
{
  "type": "basic",
  "title": "Collecting Data"
}
[/block]
Here's a list of the metrics and dimensions we would like to collect from each visitor that enters our website:
[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "timestamp",
    "0-1": "Dimension",
    "0-2": "Visit timestamp",
    "1-0": "visits",
    "1-1": "Metric",
    "1-2": "Visit count, will be `1` if you plan to push each visit separately instead of using batches",
    "2-0": "load_time",
    "2-1": "Metric",
    "2-2": "The time it took for the visitor to load our page",
    "3-0": "browser",
    "3-1": "Dimension",
    "3-2": "The name of the browser that was used to view the page",
    "4-0": "device",
    "4-1": "Dimension",
    "4-2": "The name of the device that was used to view the page",
    "5-0": "operating_system",
    "5-1": "Dimension",
    "5-2": "The visitor's operating system",
    "6-0": "ip_address",
    "6-1": "Dimension",
    "6-2": "The IP address of the visitor",
    "7-0": "path",
    "7-1": "Dimension",
    "7-2": "The page that was loaded by the visitor",
    "8-0": "",
    "8-1": "",
    "8-2": ""
  },
  "cols": 3,
  "rows": 8
}
[/block]
Data collection should be done server-side since we do not want to expose our `writerAPI` API Token. Here's an example of how your JSON document should look like as you push it to Joola
[block:code]
{
  "codes": [
    {
      "code": "{\n\t\"timestamp\": null, // null will set the current timestamp\n  \"visits\": 1,\n  \"load_time\": 855,\n  \"browser\": \"Chrome\",\n  \"device\": \"Mobile\",\n  \"operating_system\": \"iOS\",\n  \"ip_address\": \"80.179.44.10\",\n  \"path\": \"/home\"\n}",
      "language": "json"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Visualizing Data"
}
[/block]
To visualize our collected data we will use a Canvas. Canvases allow you to group visualizations into a fully working application with out-of-the-box interaction between the different visualizations

In this example, our dashboard will contain the following visualizations:
[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Visualization type",
    "h-2": "Description",
    "0-0": "Visits over time",
    "0-1": "Timeline",
    "0-2": "Aggregation of daily visits on a Timeline",
    "1-0": "Visits",
    "1-1": "Metric",
    "1-2": "Sum of visits",
    "2-0": "Avg. Load time",
    "2-1": "Metric",
    "2-2": "The average amount of time it took a visitor to load our pages",
    "3-0": "Mobile visitors",
    "3-1": "Metric",
    "3-2": "% of visits originated from mobile devices",
    "4-0": "Tablet visitors",
    "4-1": "Metric",
    "4-2": "% of visits originated from tablet devices",
    "5-0": "Browsers",
    "5-1": "Pie",
    "5-2": "Distribution of browsers used by visitors",
    "6-2": "Distribution of devices used by visitors",
    "6-1": "Pie",
    "6-0": "Devices",
    "7-1": "Pie",
    "7-0": "Operating systems",
    "7-2": "Distribution of operating systems used by visitors",
    "8-0": "Paths",
    "8-1": "Table",
    "8-2": "A table showing popular page paths"
  },
  "cols": 3,
  "rows": 9
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Result"
}
[/block]

[block:html]
{
  "html": "<a href=\"#\" name=\"result\"></a><p data-height=\"2320\" data-theme-id=\"9065\" data-slug-hash=\"gbbbXN\" data-default-tab=\"result\" data-user=\"orweinberger\" class='codepen'>See the Pen <a href='http://codepen.io/orweinberger/pen/gbbbXN/'>Joola web analytics dashboard example</a> by Or Weinberger (<a href='http://codepen.io/orweinberger'>@orweinberger</a>) on <a href='http://codepen.io'>CodePen</a>.</p>"
}
[/block]