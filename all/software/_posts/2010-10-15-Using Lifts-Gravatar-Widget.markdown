---
layout: post
title: Using Lift's Gravatar Widget
---

## {{ page.title }}

15 October 2010
{: .publish_date}

After reading Timothy Perrett's [post](http://blog.getintheloop.eu/2010/10/13/using-lift-s-autocomplete-widget) on using the autocomplete widget I thought I'd add gravatar to a side-project and write a post about it.  So here's another post about Lift making life easy.

Adding Gravatar to a Lift powered site is easy:
{% highlight scala %}
Gravatar("email@domain.com") // => Produces a gravatar thats 42x42 with a G rating
{% endhighlight %}

Need to change the size or rating?  Also easy:

{% highlight scala %}
Gravatar("email@domain.com", 50) // => Produces a gravatar thats 50x50 with a G rating    
Gravatar("email@domain.com", 50, "R") // => Produces a gravatar thats 50x50 with a R rating
{% endhighlight %}



