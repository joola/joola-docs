Calculated metrics offer you the option to query existing metric(s) and based on their values, perform a calculation that is later returned as part of the results. In order to query a calculated metric you'll need to use the formula attribute:

|  PROPERTY | TYPE  | DEFAULT  | DESCRIPTION |
|---|---|---|---|
| `metric.formula` | Object | | A reference to a formula Object. |
| `metric.formula.dependsOn` | Array | | An array of metric names or objects. Each will be passed to the run function according to the order specified in the array. |
| `metric.formula.run` | String | | A string containing a javascript function. The function is called with the metrics specifying in the dependsOn parameter and need to return a value which is then returned as part of the result set. |
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "The calculated metric **key** and **name** needs to be different than any existing metric name"
}
[/block]
#Example
[block:code]
{
  "codes": [
    {
      "code": "$('#example').Metric({\n  query: {\n\t\ttimeframe: 'last_30_days',\n    metrics: [\n      {\n        key: 'percentWatched',\n        decimals: 2,\n        suffix: '%',\n        formula: {\n          dependsOn: ['movieLength', 'lengthWatched'],\n          run: 'function(mlength, watched) { return watched/mlength*100 }'\n        }\n      }\n    ],\n    collection: 'JoolaFlix'\n  }\n});",
      "language": "javascript"
    }
  ]
}
[/block]