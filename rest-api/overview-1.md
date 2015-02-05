This guide describes the resources that make up the Joola REST API. If you have any problems or requests please [contact us](mailto:support@joo.la).
[block:api-header]
{
  "type": "basic",
  "title": "Using This Guide"
}
[/block]
We will be using `https://my.app.joo.la` as the default application for the examples shown below. You should replace this URL with the one specific for your Joola application. The default `APIToken` used is *myapitoken*, please replace this with the appropriate one.
[block:api-header]
{
  "type": "basic",
  "title": "Current Version"
}
[/block]
To check what version of Joola is running, run:
[block:code]
{
  "codes": [
    {
      "code": "$ curl https://my.app.joo.la:8081/system/version?APIToken=myapitoken\n\n{\"version\": \"joola version 0.8.1\"}",
      "language": "shell"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Schema"
}
[/block]
All data is sent and received as JSON.
[block:code]
{
  "codes": [
    {
      "code": "$ curl -i https://my.app.joo.la/system/version?APIToken=myapitoken\n\nHTTP/1.1 200 OK\nServer: joola\nAccess-Control-Allow-Credentials: true\nAccess-Control-Expose-Headers: ETag, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset\nX-joola-Request-Id: HpEO6kDLn:1399190956781:Uj184Jhop\nX-RateLimit-Limit: 5000\nX-RateLimit-Remaining: 4987\nX-RateLimit-Reset: 1399192026\nRetry-After: 1069\nX-joola-Duration: 14\nX-joola-Requested-By: HpEO6kDLn\nX-joola-Fulfilled-By: HpEO6kDLn\nX-joola-Duration-Fulfilled: 2\nContent-Type: application/json\nContent-Length: 36\nETag: \"867689076\"\nDate: Sun, 04 May 2014 08:09:16 GMT",
      "language": "shell"
    }
  ]
}
[/block]
Blank fields are included as null instead of being omitted.

All timestamps are returned in *ISO 8601* format:
[block:code]
{
  "codes": [
    {
      "code": "YYYY-MM-DDTHH:MM:SSZ",
      "language": "text"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "HTTP Verbs"
}
[/block]
joola API uses the following Verbs.
[block:parameters]
{
  "data": {
    "0-0": "`HEAD`",
    "1-0": "`GET`",
    "2-0": "`POST`",
    "3-0": "`PATCH`",
    "4-0": "`PUT`",
    "5-0": "`DELETE`",
    "5-1": "Used for deleting resources.",
    "4-1": "Used for replacing resources or collections. For PUT requests with no body attribute, be sure to set the Content-Length header to zero. Rarely used as part of the framework.",
    "3-1": "Used for updating resources with partial JSON data. For instance, an Issue resource has title and body attributes. A PATCH request may accept one or more of the attributes to update the resource.",
    "2-1": "Used for creating resources, or performing custom actions.",
    "1-1": "Used for retrieving resources.",
    "0-1": "Can be issued against any resource to get just the HTTP header info.",
    "h-0": "Verb",
    "h-1": "Description"
  },
  "cols": 2,
  "rows": 6
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Authentication"
}
[/block]
There are three ways to authenticate through joola API. Requests that require authentication will return 404 Not Found, instead of 403 Forbidden, in some places. This is to prevent the accidental leakage of private information to unauthorized users.

## Basic Authentication
[block:code]
{
  "codes": [
    {
      "code": "$ curl -u \"workspace/username:password\" https://my.app.joo.la/system/version",
      "language": "shell"
    }
  ]
}
[/block]
## APIToken (sent in a header)
[block:code]
{
  "codes": [
    {
      "code": "$ curl -H \"Authorization: token my-apitoken\" https://my.app.joo.la/system/version",
      "language": "shell"
    }
  ]
}
[/block]
## APIToken (sent as a parameter)
[block:code]
{
  "codes": [
    {
      "code": "$ curl https://my.app.joo.la/system/version?APIToken=my-apitoken",
      "language": "shell"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Rate Limits"
}
[/block]
You can check the returned HTTP headers of any API request to see your current rate limit:
[block:code]
{
  "codes": [
    {
      "code": "$ curl -i https://my.app.joo.la/system/version?APIToken=myapitoken\n\nHTTP/1.1 200 OK\nDate: Sun, 04 May 2014 07:39:52 GMT\nX-RateLimit-Limit: 5000\nX-RateLimit-Remaining: 4989\nX-RateLimit-Reset: 1399192026",
      "language": "shell"
    }
  ]
}
[/block]
The headers include the information about the current rate limit status:
[block:parameters]
{
  "data": {
    "0-0": "`X-RateLimit-Limit`https://localhost:8081",
    "1-0": "`X-RateLimit-Remaining`",
    "2-0": "`X-RateLimit-Reset`",
    "3-0": "`Retry-After`",
    "3-1": "The number of seconds before the current rate limit resets.",
    "2-1": "The time at which the current rate limit window resets in UTC epoch seconds.",
    "1-1": "The number of requests remaining in the current rate limit window.",
    "0-1": "The maximum number of requests that the consumer is permitted to make per hour.",
    "h-0": "Header",
    "h-1": "Description"
  },
  "cols": 2,
  "rows": 4
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Response Headers"
}
[/block]
Each API request fulfilled by joola contains some useful response headers:
[block:parameters]
{
  "data": {
    "0-0": "`X-joola-Request-Id`",
    "1-0": "`X-joola-Duration`",
    "2-0": "`X-joola-Duration-Fulfilled`",
    "3-0": "`X-joola-Requested-By`",
    "4-0": "`X-joola-Fulfilled-By`",
    "4-1": "Node UUID of the fulfiller.",
    "3-1": "Node UUID of the requester.",
    "2-1": "Total duration of request from dispatch in/out.",
    "1-1": "Total duration of request from route in to out.",
    "0-1": "Unique request id assigned by joola server. Format: {NODE_UUID}:{TIMESTAMP}:{UUID}",
    "h-0": "Header",
    "h-1": "Description"
  },
  "cols": 2,
  "rows": 5
}
[/block]