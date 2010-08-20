---
layout: post
title: CouchDB Custom Query Params in Lift
---

## {{ page.title }}

19 August 2010
{: .publish_date}

One of the new features of Lift is the ability to use custom parameters when making a CouchDB query using the withParams method of Queryable.
This allows you to do things like have your couch query output docs sorted by one field while limiting the output to docs that contain a specific value.

Lets say you store all of your homework assignments in couch and your query to be sorted by date.  Your couch design might look like this:

{% highlight javascript %}
function(doc) { 
	if (doc.type == 'Homework'){
		emit(doc.date, doc)
	};
}
{% endhighlight %}

If you want to limit what gets return by a specific class you can now make a call like:
{% highlight scala %}
var tempParam:Map[String, Any] = Map[String, Any]("Class"->JString("English"))
var viewReturn = Homework.queryView("HomeworkDbViews", "FindAllHomeworkDesign", _.withParams(tempParam))
{% endhighlight %}

This adds some nice flexibility to using CouchDB with Lift.

For more details check out the [Queryable API](http://main.scala-tools.org/mvnsites/liftweb-2.0/framework/scaladocs/net/liftweb/couchdb/Queryable.html)

Note: In Lift 2.0 withParams is a protected method so you need to be using the 2.1 Snapshot
