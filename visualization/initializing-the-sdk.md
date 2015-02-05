Joola's SDK helps you query, visualize and manage your data stored within your Joola application.
In order to get started, you will need to include the SDK within your webpage/project, like this:
[block:code]
{
  "codes": [
    {
      "code": "<script src=\"<APPLICATION_URL>/joola.min.js?APIToken=<READER_API_TOKEN>\" />",
      "language": "html"
    }
  ]
}
[/block]
**Copy, modify and paste** the statement above within your webpage. Replace <APPLICATION_URL> and <READER_API_TOKEN> with values specific to your application.
When the script runs, it:
- Connects to the application.
- Ensures valid credentials were used. 
- Makes the SDK ready for your use. 
 
Initialization can also be done manually by calling `joola.init(options, callback)`:
[block:code]
{
  "codes": [
    {
      "code": "<html>\n  <head>\n    <script src=\"<APPLICATION_URL>/joola.min.js\"></script>\n    <script type=\"text/javascript\">\n      joola.init({\"APIToken\": \"<READER_API_TOKEN>\"}, function(err) {\n        if (err) \n          throw err;\n        console.log('Joola initialized', joola.VERSION);\n      });\n    </script>\n  </head>\n  <body>\n    ...\n  </body>\n</html>",
      "language": "html"
    }
  ]
}
[/block]
That's it, your SDK is available and ready for use.
[block:api-header]
{
  "type": "basic",
  "title": "What's next?"
}
[/block]
- [Controlling Look & Feel]()
- [Events]()
- [Visualizing data](doc:overview)