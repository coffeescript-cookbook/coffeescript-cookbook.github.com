---
layout: recipe
title: Adapter patter
chapter: Design patterns
---
## Problem

Suppose we have 3-rd party grid component. We want to apply there our own custom sorting but a small problem. Our custom sorter does not implement required interface by grid component.
To understand the problem completely best example would be an socket from our usual life. Everybody knows this device. In some countries it has 3 pins and in other contries it has only 2 pins. 
This is exactly right situation to use [adapter pattern](https://en.wikipedia.org/wiki/Adapter_pattern). 

## Solution

{% highlight coffeescript %}
# a fragment of 3-rd party grid component
class AwesomeGrid
	constructor: (@datasource)->
		@sort_order = 'ASC' 
		@sorter = new NullSorter # in this place we use NullObject pattern (another usefull pattern)
	setCustomSorter: (@customSorter) ->
		@sorter = customSorter
	sort: () ->
		@datasource = @sorter.sort @datasource, @sort_order
		# don't forget to change sort order


class NullSorter
	sort: (data, order) -> # do nothing; it is just a stub
	
class RandomSorter
	sort: (data)->
		for i in [data.length-1..1] #let's shuffle the data a bit
    			j = Math.floor Math.random() * (i + 1)
    			[data[i], data[j]] = [data[j], data[i]]
		return data

class RandomSorterAdapter
	constructor: (@sorter) ->
	sort: (data, order) ->
		@sorter.sort data

agrid = new AwesomeGrid ['a','b','c','d','e','f']
agrid.setCustomSorter new RandomSorterAdapter(new RandomSorter)
agrid.sort() # sort data with custom sorter through adapter

{% endhighlight %}

## Discussion

Adapter is usefull when you have to organize an interaction between two objects with different interfaces. It can happen when you use 3-rd party libraries  or you work with legacy code. 
In any case be carefull with adapter: it can be helpfull but it can instigate design errors. 
