Pushing events into Joola can be done in two ways, via our REST API or via our Javascript SDK
[block:api-header]
{
  "type": "basic",
  "title": "REST API"
}
[/block]
Using the REST API:
[block:code]
{
  "codes": [
    {
      "code": "curl -i -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n  \\\"movieTitle\\\": \\\"The Matrix\\\",\n  \\\"movieLength\\\": 112,\n  \\\"lengthWatched\\\": 29,\n  \\\"views\\\": 1,\n  \\\"userId\\\": \\\"194337\\\",\n  \\\"userCountry\\\": 'Germany',\n  \\\"deviceUsed\\\": \\\"Mobile\\\"\n}]\" https://<APPLICATION_URL>/insert/JoolaFlix/<COLLECTION>?APIToken=<WRITER_API_TOKEN>",
      "language": "shell",
      "name": "cURL"
    },
    {
      "code": "<?php\n\nfunction beaconInsert($host, $apitoken, $collection, $doc) {\n    $ch = curl_init($host . '/beacon/workspace/' . $collection . '?APIToken=' . $apitoken);\n    curl_setopt($ch, CURLOPT_CUSTOMREQUEST, \"POST\");\n    curl_setopt($ch, CURLOPT_POSTFIELDS, $doc);\n    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);\n    curl_setopt($ch, CURLOPT_HTTPHEADER, array(\n        'Content-Type: application/json',\n        'Content-Length: ' . strlen($doc))\n    );\n    $result = curl_exec($ch);\n    curl_close($ch);\n}\n\nbeaconInsert('https://<APPLICATION_URL>', '<WRITER_API_TOKEN>', '<COLLECTION>', '{\"movieTitle\": \"The Matrix\",\"movieLength\": 112, \"lengthWatched\": 29, \"views\": 1, \"userId\": \"194337\", \"userCountry\": \"Germany\", \"deviceUsed\": \"Mobile\"}')\n\n?>  ",
      "language": "php",
      "name": "PHP"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Javascript SDK"
}
[/block]
Pushing events is done via `joola.insert` which will return a callback function with `err` and `result`, `result` will contain the events as it was inserted to Joola.
[block:code]
{
  "codes": [
    {
      "code": "var event = {\n  \"movieTitle\": \"The Matrix\",\n  \"movieLength\": 112,\n  \"lengthWatched\": 29,\n  \"views\": 1,\n  \"userId\": \"194337\",\n  \"userCountry\": \"Germany\",\n  \"deviceUsed\": \"Mobile\"\n}\n \njoola.insert(\"JoolaFlix\", event, function(err,res) {\n  if (err) \n  \tthrow err;\n  console.log('Event pushed successfuly', res);\n});",
      "language": "javascript",
      "name": "Javascript"
    },
    {
      "code": "var joola = require('joola.sdk');\n\njoola.init({\"host\": \"https://<APPLICATION_URL>\", \"APIToken\": \"<WRITER_API_TOKEN>\"}, function(err,res) { \n    var doc = {\n        \"movieTitle\": \"The Matrix\",\n        \"movieLength\": 112,\n        \"lengthWatched\": 29,\n        \"views\": 1,\n        \"userId\": \"194337\",\n        \"userCountry\": \"Germany\",\n        \"deviceUsed\": \"Mobile\",\n        \"collection\": \"JoolaFlix\"\n    }\n \n    joola.insert(\"JoolaFlix\", doc, function(err,res) {\n        if (err) throw err\n        console.log('Document pushed successfuly', res);\n    });\n});",
      "language": "javascript",
      "name": "Node.JS"
    }
  ]
}
[/block]