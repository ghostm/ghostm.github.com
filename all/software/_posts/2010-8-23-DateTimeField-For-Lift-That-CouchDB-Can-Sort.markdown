---
layout: post
title: DateTimeField For Lift That CouchDB Can Sort
---

## {{ page.title }}

23 August 2010
{: .publish_date}

The other day I ran into a slight problem with the interaction between Lift and CouchDB.  I wanted to have Couch emit a list of records [sorted by date](http://wiki.apache.org/couchdb/View_collation#Sorting_by_Dates), but the format of Lift's DateTimeField doesn't sort lexicographically.

To remedy this (and as an exercise in Scala and Lift) I decided to write a new class that extended DataTimeField, but converted the date to and from a format that would work better with Couch.

I ran into a few small hurdles that were due to my lack of Scala knowledge, but the entire process took less time than I expected.  

I decided to use the ISO 8601 format and the most important change was going from:
{% highlight scala %}
SimpleDateFormat("EEE, d MMM yyyy HH:mm:ss z", Locale.US)
{% endhighlight %}

to:

{% highlight scala %}
SimpleDateFormat("yyyy-MM-dd'T'HH:mm:ssz", Locale.US)
{% endhighlight %}

To make things easier for the next person I threw the class onto [Github](http://github.com/ghostm/ISO8601DateTimeField)
