---
layout: default
title: Wanted Recipes
---
# Wanted Recipes

Here's a list of recipes we think we need. Pick one, implement it, and remove it from the page. Alternately, add a quick note here for a recipe you'd like to see so someone else can add it.

In the notes below, "JS" means the recipe is just a simple passthrough to an existing JavaScript method.

## Syntax

* Ensuring variables are closed over # with "do"

## Objects

## Strings

* HTML methods # JS .sup(), .sub(), .blink(), .link(url), etc. May not exist in your JS impl!
* substr # str.substr(x,y)  === str[x..x+y-1] === str[x...x+y]
* substring # str.substring(x,y) === str.slice(x,y)  === str[x..y-1] === str[x...y]
* Replacing substrings

## Arrays

* Testing every element in an array
{% highlight coffeescript %}
evens = (x for x in [0..10] by 2)
even = (x) -> x % 2 == 0
evens.every even
# => true
{% endhighlight %}
* Filtering arrays # [1..10.filter (x) -> x % 2 == 0 # => [ 2, 4, 6, 8, 10 ]
* Detecting presence of matching items in an array # [1..10].some (x) -> x % 2 == 0 # => true
* Processing an array item by item # [10..1].forEach (x) -> console.log x # => nothing;, but a countdown is displayed on the console
* Replace all duplicates of an array

## Dates and Times

* Calculating the phase of the moon
* Number of days between two dates

## Math

* square root # JS Math.sqrt
* Constants # JS Math.PI, Math.E
* floor, ceil, round # JS Math.floor, Math.ceil, Math.round
* Raising a number to a power # JS Math.pow(x, y)
* Logarithms # Math.log
* Finding the base-n log # Math.log(num) / Math.log(base)
* Exponents # Math.exp
* Check if a creditcard is valid (checksum, Luhn algorithm)

## Functions

* Nested functions

{% highlight coffeescript %}
hypotenuse = (a, b) ->
  square = (x) -> x * x
  Math.sqrt(square(a) + square(b))

console.log hypotenuse 3, 4
# => 5

square 5
# ReferenceError: square is not defined
{% endhighlight %}

* Optional Arguments # use arg? to detect presence: if arg=0, arg? == true

{% highlight coffeescript %}
foo = (a, b=42, c) -> if c? then a*b*c else a*b
[Function]
foo 6
# => 252
foo 1, 2
# => 2
foo 1, 2, 3
# => 6
{% endhighlight %}

## jQuery

## Regular Expressions

* Searching for substrings # "foo bar baz".match(/ba./) # => [ 'bar', index: 4, input: 'foo bar baz' ]
* Searching for substrings # "foo bar baz".search(/ba./) # => 4
* Replacing substrings # "foo bar baz".replace( /ba./, 'foo') # => "foo foo baz"

## Networking

* Basic HTTP server
* Basic HTTP client

## AJAX

* Getting data from a remote server # using raw XHTTPRequest instead of jQuery's $.ajax

## Design patterns

* Creational Patterns
** Abstract Factory
** Prototype
** Singleton

* Structural Patterns
** Adapter
** Composite
** Facade
** Flyweight
** Proxy

* Behavioral Patterns
** Chain of Responsibility
** Command
** Iterator
** Mediator
** Observer
** State
** Template Method
** Visitor
