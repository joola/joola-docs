Joola's SDK uses Events for communication with the hosting webpage. Here are the available events:

[block:parameters]
{
  "data": {
    "h-0": "Event",
    "h-1": "Description",
    "h-2": "Signature",
    "0-0": "`ready`",
    "0-1": "Fires once when Joola is ready for use.",
    "0-2": "`function(err, ref)`\n- `err` includes any error experienced.\n- `ref` holds reference to the Joola object.",
    "1-0": "`connected`",
    "1-1": "Fires when Joola is (re)connected to the application.",
    "2-0": "`disconnected`",
    "2-1": "Fires when Joola is disconnected from the application.",
    "2-2": "`function(reason)`\n- `reason` holds the reason for the disconnection, if known.",
    "3-0": "`error`",
    "3-1": "Fires when an unhandled general exception is thrown.",
    "3-2": "`function(err)`\n- `err` holds the error."
  },
  "cols": 3,
  "rows": 4
}
[/block]
Here's an example of how Events can be used as part of your HTML page.
[block:code]
{
  "codes": [
    {
      "code": "<html>\n  <head>\n    <script src=\"https://<APP_URL>.app.joo.la/joola.min.js\"></script>\n    <script type=\"text/javascript\">\n      joola.init({\"APIToken\": \"<YOUR_API_TOKEN>\"}, function(err) {\n        if (err) \n          throw err;\n        console.log('Joola initialized', joola.VERSION);\n      });\n      joola.on('ready', function(err, ref){\n        if (err)\n          throw err;\n        console.log('Joola is ready for work');\n      });\n      joola.on('connected', function(){\n        console.log('Joola connected.');\n      });\n      joola.on('disconnected', function(reason){\n        console.log('Joola disconnected.');\n      });\n      joola.on('error', function(error){\n        console.log('Joola general error occured.');\n      });\n    </script>\n  </head>\n  <body>\n    ...\n  </body>\n</html>",
      "language": "html"
    }
  ]
}
[/block]