---
title: Testing a sitemap with bash, sed and curl
layout: post
---

During the migration from WordPress to Jekyll I wanted to confirm ensure I didn't break any existing permalinks and leave 404s hanging around. The process is trivial but something I may want to repeat.

First, download the sitemap.xml.gz output by the All In One SEO WordPress pluging. Crack this XML in a simplistic way and write out all of the known URLs to a simple text file.

{% highlight bash %}
gunzip sitemap.xml.gz
grep \<loc\> sitemap.xml | sed 's/.*<loc>//' | sed 's|</loc>||' > sitemap.txt
{% endhighlight %}

Next, create a script `testsitemap.sh` that reads from stdin and makes an HTTP request for each line and records the HTTP response code.

{% highlight bash %}
#!/bin/bash
while read line
do
    response=$(curl --write-out %{http_code} --silent --output /dev/null $line)
    echo $line '\t' $response
    sleep 1
done
{% endhighlight %}

Finally, pull the whole thing together and list and 404s.

{% highlight bash %}
cat sitemap.txt | bash testsitemap.sh | grep 404
{% endhighlight %}
