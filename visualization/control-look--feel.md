Joola's SDK allows you to control every detail of the embedded visualization's look & feel.
[block:api-header]
{
  "type": "basic",
  "title": "The default theme"
}
[/block]
Joola ships with a custom default theme to give developers a nice look & feel out-of-the-box.
Developers can choose either to use the default theme and build on top of it with their own custom CSS classes or to not load the default theme at all and design their data application from scratch by setting:
[block:code]
{
  "codes": [
    {
      "code": "<script src=\"<APPLICATION_URL>/joola.min.js?APIToken=<READER_API_TOKEN>&includecss=false\" />",
      "language": "html"
    }
  ]
}
[/block]
Or if initializing manually:
[block:code]
{
  "codes": [
    {
      "code": "<script src=\"https://<APPLICATION_URL>/joola.min.js\"></script>\n<script type=\"text/javascript\">\n  joola.init({\n  \tAPIToken: \"<READER_API_TOKEN>\", \n    includecss: false\n  }, function(err) {\n    if (err) \n      throw err;\n    console.log('Joola initialized', joola.VERSION);\n  });\n</script>",
      "language": "html"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Twitter Bootstrap"
}
[/block]
We use Twitter Bootstrap as basis for the default theme, so to get best results make sure you include Twitter Bootstrap on the webpage.
[block:code]
{
  "codes": [
    {
      "code": "<link rel=\"stylesheet\" href=\"//maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.min.css\">",
      "language": "html"
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "jQuery"
}
[/block]

[block:callout]
{
  "type": "warning",
  "body": "We're in the process of de-coupling Joola SDK from jQuery and offering existing capabilities as a jQuery plugin."
}
[/block]
Joola's SDK is coupled with jQuery and when loaded it looks if the webpage already includes it, if not Joola will add jQuery to the webpage and use it during runtime.