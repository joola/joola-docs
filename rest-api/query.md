Query your data via REST API
[block:code]
{
  "codes": [
    {
      "code": "curl -i -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n  \\\"timeframe\\\": \\\"last_30_days\\\",\n  \\\"metrics\\\": [\\\"views\\\"],\n  \\\"dimensions\\\": [\\\"userCountry\\\"],\n  \\\"collection\\\": \\\"JoolaFlix\\\"\n}]\" https://<APP_URL>/query?APIToken=<READER_API_TOKEN>",
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
      "code": "curl -i -X POST -H \"Content-Type: application/json\" --data-binary \"[{ \n  \\\"timeframe\\\": \\\"last_30_days\\\",\n  \\\"metrics\\\": [\\\"views\\\"],\n  \\\"dimensions\\\": [\\\"userCountry\\\"],\n  \\\"collection\\\": \\\"JoolaFlix\\\"\n}]\" https://joola-demo.app.joo.la/query?APIToken=ypy5KW44BoPx4sT5Ma44SWKON0P5zhzk",
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
      "code": "[\n  {\n    \"dimensions\":[\n      {\n        \"key\":\"userCountry\",\n        \"dependsOn\":\"userCountry\",\n        \"name\":\"userCountry\",\n        \"adhoc\":true,\n        \"datatype\":\"string\",\n        \"attribute\":\"userCountry\"\n      }\n    ],\n    \"metrics\":[\n      {\n        \"key\":\"views\",\n        \"dependsOn\":\"views\",\n        \"name\":\"views\",\n        \"adhoc\":true,\n        \"attribute\":\"views\",\n        \"_key\":\"views\"\n      }\n    ],\n    \"documents\":[\n      {\n        \"values\":{\n          \"userCountry\":\"Australia\",\n          \"views\":172\n        },\n        \"fvalues\":{\n          \"userCountry\":\"Australia\",\n          \"views\":172\n        }\n      },\n      {\n        \"values\":{\n          \"userCountry\":\"Brazil\",\n          \"views\":88\n        },\n        \"fvalues\":{\n          \"userCountry\":\"Brazil\",\n          \"views\":88\n        }\n      },\n      {\n        \"values\":{\n          \"userCountry\":\"China\",\n          \"views\":192\n        },\n        \"fvalues\":{\n          \"userCountry\":\"China\",\n          \"views\":192\n        }\n      },\n      {\n        \"values\":{\n          \"userCountry\":\"Cyprus\",\n          \"views\":103\n        },\n        \"fvalues\":{\n          \"userCountry\":\"Cyprus\",\n          \"views\":103\n        }\n      }\n    ],\n    \"uid\":\"x4EJwOKjZ0OBdoFd8QQmPSaylddfDGrL\",\n    \"resultCount\":4,\n    \"query\":{\n      \"collection\":\"JoolaFlix\",\n      \"dontcache\":true,\n      \"filter\":[\n\n      ],\n      \"realtime\":false,\n      \"interval\":\"timebucket.minute\",\n      \"timeframe\":{\n        \"start\":\"2014-10-07T15:06:01.000Z\",\n        \"end\":\"2014-11-06T15:06:01.999Z\"\n      },\n      \"metrics\":[\n        {\n          \"key\":\"views\",\n          \"dependsOn\":\"views\",\n          \"name\":\"views\",\n          \"adhoc\":true,\n          \"attribute\":\"views\",\n          \"_key\":\"views\"\n        }\n      ],\n      \"dimensions\":[\n        {\n          \"key\":\"userCountry\",\n          \"dependsOn\":\"userCountry\",\n          \"name\":\"userCountry\",\n          \"adhoc\":true,\n          \"datatype\":\"string\",\n          \"attribute\":\"userCountry\"\n        }\n      ],\n      \"uid\":\"x4EJwOKjZ0OBdoFd8QQmPSaylddfDGrL\",\n      \"ts\":{\n        \"start\":\"2014-11-06T15:06:01.062Z\",\n        \"end\":\"2014-11-06T15:06:01.086Z\",\n        \"duration\":24\n      },\n      \"_interval\":\"minute\"\n    }\n  }\n]",
      "language": "json",
      "name": "200 OK"
    },
    {
      "code": "{\n\t\"documentation_url\":\"http://docs.joo.la\",\"message\":\"Request for action by unauthenticated user.\"\n}",
      "language": "shell",
      "name": "401 Unauthorized"
    }
  ]
}
[/block]