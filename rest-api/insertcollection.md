Insert a document via REST API
[block:code]
{
  "codes": [
    {
      "code": "curl -i -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n  \\\"movieTitle\\\": \\\"The Matrix\\\",\n  \\\"movieLength\\\": 112,\n  \\\"lengthWatched\\\": 29,\n  \\\"views\\\": 1,\n  \\\"userId\\\": \\\"194337\\\",\n  \\\"userCountry\\\": \\\"Germany\\\",\n  \\\"deviceUsed\\\": \\\"Mobile\\\"\n}]\" https://<APP_URL>/insert/<COLLECTION>?APIToken=<WRITER_API_TOKEN>",
      "language": "shell"
    }
  ]
}
[/block]
#EXAMPLE
[block:code]
{
  "codes": [
    {
      "code": "curl -i -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n\t\\\"movieTitle\\\": \\\"The Matrix\\\",\n  \\\"movieLength\\\": 112,\n  \\\"lengthWatched\\\": 29,\n  \\\"views\\\": 1,\n  \\\"userId\\\": \\\"194337\\\",\n  \\\"userCountry\\\": \\\"Germany\\\",\n  \\\"deviceUsed\\\": \\\"Mobile\\\"\n}]\" https://joola-demo.app.joo.la/insert/demo?APIToken=WHUWSPtYcOmu3XDQSpEd8GlqeeWLzb5W",
      "language": "shell"
    }
  ]
}
[/block]
#RESPONSES
[block:code]
{
  "codes": [
    {
      "code": "[\n  {\n    \"movieTitle\": \"The Matrix\",\n    \"movieLength\": 112,\n    \"lengthWatched\": 29,\n    \"views\": 1,\n    \"userId\": \"194337\",\n    \"userCountry\": \"Germany\",\n    \"deviceUsed\": \"Mobile\",\n    \"timestamp\":\"2014-10-30T20:59:11.041Z\",\n    \"timestamp_timebucket\":\n      {\n        \"dow\":4,\n        \"hod\":20,\n        \"second\":\"2014-10-30T20:59:11.000Z\",\n        \"minute\":\"2014-10-30T20:59:00.000Z\",\n        \"hour\":\"2014-10-30T20:00:00.000Z\",\n        \"ddate\":\"2014-10-30T00:00:00.000Z\",\n        \"month\":\"2014-10-01T00:00:00.000Z\",\n        \"year\":\"2014-01-01T00:00:00.000Z\"\n      },\n    \"ourTimestamp\":\"2014-10-30T20:59:11.041Z\",\n    \"_key\":\"78c79302701f640ee32e01f987fc61ce\",\n    \"_id\":\n      {\n        \"_bsontype\":\"ObjectID\",\n        \"id\":\"TR¦1î` \\u0007¶Ù\"\n      },\n    \"saved\":true\n  }\n]",
      "language": "json",
      "name": "200 OK"
    },
    {
      "code": "{\n \"documentation_url\": \"https://docs.joo.la\",\n \"message\": \"Request for action by unauthenticated user.\"\n}",
      "language": "json",
      "name": "401 Unauthorized"
    }
  ]
}
[/block]