---
layout: post
title: "Adventures with Jekyll"
comments: true
category:
tags: []
---
>When I was younger, I tore down and rebuilt the engine of my 1980 Mini Cooper. While it involved some tools and an instruction manual, understanding the engineering and process was easily within the capabilities of a 17-year-old. With computer controlled, fuel injected engines, I don't think that's even remotely feasible today.

Over the years I've hosted this site on Blogger, Movable Type, PHP, ASP.NET, and most recently, have been using WordPress to host this blog on andyoakley.com. WordPress been very easy to maintain, cheap to host, and rich in functionality. Overall, I have few complaints, especially given the frequency with which I had been making updates. The only real gripe I had was around page load time which was hovering around 8s! I know there are multiple good caching solutions for WordPress of which I tried several with mixed success.

I wanted two things:
1. Make the site fast. Optimizing for serve rather than edit.
1. Simplify. Reduce the complexity and get back to an easily-understood rendering model just like a 1980 four cylinder engine.

As a result this site in now completely delivered as static files. No more database dependency and dramatically reduced scalability concerns. It's also wicked fast. For this purpose I picked [Jekyll](http://jekyllrb.com), a Ruby-based system for taking content and pressing out static HTML. The content itself is served up by Amazon S3 which is both scalable and cheap.

The migration was very easy. The built-in importer worked well from a wordpress.xml output. Since I hadn't been comment-enabled for a while, the only real server side functionality was the plugin that pulled latest tweets in the right hand bar but that was easy enough to convert to client-side behavior with a little help from [jQuery](http://jquery.com). That's perhaps a topic for another post.

So far I'm happy.
