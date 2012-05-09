---
title: Showing latest tweets in a static web page
layout: post
---
This site is hosted as static files served out of S3 so there's no server side processing going on. Any dynamic functionality must either by iframed in from another server or handled in Javascript. The tweets shown on the right are an example of the latter.

This is actually quite easy to do:
1. Use [jQuery](http://jquery.com) which makes Javascript programming much easier. Include a reference to the jQuery script in the page header.
1. Load up the latest tweets from the Twitter API in JSON format.
1. Translate data to HTML and render.

First we'll set up the container into which the content will be rendered on the main page:

{% highlight html %}
<ul id="tweets"></ul>
{% endhighlight %}

Next, let's take a look at the code. This leverages the very handy yet terrifying [Linkify](http://jmrware.com/articles/2010/linkifyurl/linkify.html) snippet by Jeff Roberson for URL extraction and hyperlinking. Thanks, Jeff!

<script src='https://gist.github.com/1651851.js?file=gistfile1.js'>
</script>

That's it. When the page has loaded, the AJAX call to the Twitter API is made and a simple bulleted list of tweets is rendered in the page.
