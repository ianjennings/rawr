# RAWR!

Rawr is a framework to create good looking websites quickly. Rawr uses the power of standardized margins to create a consistent and pixel perfect look.

---

To use rawr, just import the less document:

    @import "/rawr/lib/rawr";

Add this to the top of your stylesheet

-------

If you want to keep things organized, you can use the following example:

This is our directory structure:
    
    /
      index.html
      /static
          my-project.less
          /rawr

index.html would look like this:

    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>rawr!</title>
            <script src="//html5shim.googlecode.com/svn/trunk/html5.js"></script>
            <link href='http://fonts.googleapis.com/css?family=Droid+Sans:400,700|Droid+Sans+Mono|Droid+Serif:400,700,700italic' rel='stylesheet' type='text/css'>
            <script type="text/javascript">
                less = { env: 'development' };
            </script>
            <link rel="stylesheet/less" type="text/css" href="static/my-project.less">
            <script src="static/rawr/lib/external/js/less.min.js" type="text/javascript"></script>
            <script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"></script>
        </head>
        <body>
        </body>
    </html>
    
and my-project.less would look like:

    @import "rawr/lib/rawr";
    
    body {
      background-color: @informative;
    }

You can now access all the variables and standarized margins provided by rawr in your less document.
  
You can find the design documentation at [the official website](http://getrawr.com/).