---
layout: post
title: Using Couchone With Lift
---

## {{ page.title }}

16 September 2010
{: .publish_date}

A project of mine recently reached the point of sharing it with friends to get some feedback.  It's a Lift app that uses CouchDB for most of its data storage (although this weekend I think I will transition to MongoDB as it is a better fit), and I figured it would be a perfect time to try out the CouchDB hosting that [Couchone](http://www.couchone.com) provides.

I'm not storing very sensitive data, but I didn't want to expose my couch to everyone.  So I configured an admin for the database and had to figure out how to get Lift to play nicely with the basic HTTP authentication that was needed.

The solution turned out to be very simple.
{% highlight scala %}
val database = new Database("database_name")
{% endhighlight %}

turned into:

{% highlight scala %}
var req = :/("mycouchoneusername.couchone.com").as_!("username", "password")    
val database = new Database(req, "database_name")
{% endhighlight %}

