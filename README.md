# Programming as Conversation 3: Methods on Ruby's Built-In Objects

## Learning Goals

- Define Object Oriented Programming (OOP)
- Define instance
- Define class
- Define attribute / property
- Define "dot-notation" syntax
- Define method
- Demonstrate method chaining
- Find documentation about methods and attributes

## Introduction

In the previous lessons, you've learned to encapsulate work in methods. Methods
can take in arguments and then use repetition, selection, and expression
evaluation to provide information about the arguments they were handed.

But Ruby is an Object-Oriented Language. That means that many of the default
types of data can run methods that are "inside" them. They can tell you things
about themselves or they can transform themselves. We've already seen that the
constants of `3.14` or `8675309` or `"Love Will Tear Us Apart"` can tell you
things about themselves.

```ruby
3.14.class #=> Float
```

This. Is. So. Cool.

In time, you'll learn to create objects of your own, things that represent
`Student`s or `PayrollRecord`s. This is known as Object-Oriented Programming.
This is a vast topic that will take many lessons and a lot of practice to
learn. Our point here is to show you how to interact with the default objects
Ruby provides. But don't worry, you'll _definitely_ learn to teach the objects
of your world to tell you about themselves soon enough.

## Define Object-Oriented Programming

Bundling code into little objects like this that are "smart" is "Object-Oriented
Programming (OOP)." OOP is a huge topic that will take a lot of practice to
master. However, for the moment we merely want to show you how to use the
objects that Ruby provides to help you do work.

## Define Instance

Sometimes programmers call "objects" instances because they are instances of a
class. `3.14` is an instance of the `Float` class. `"hi"` is an instance of
the `String` class.

## Define Class

A class is an abstraction that establishes what all of its instances are like.
This is an ancient and difficult philosophical question. How is a tall redwood
tree, also like an oak tree, also like a magnolia tree? Some lose their leaves,
others do not. Nevertheless, we all know they are "trees." If we travel to a
remote country and see a beautiful thing with bark, leaves, and cherry
blossoms, we immediately know it's a tree without being told. Somehow there's a
blueprint of the idea of Tree-ness that all the trees we know honor.

> **PHILOSOPHY TIP**: Yes. This programming idea is built on Plato's theory of
> forms.

It's a deep philosophical question, but a class defines what related instances
know about themselves (_attributes_, more below) and can do (_methods_, more
below).

All "instances" in Ruby can tell you their class by adding `.class` to the end
of their name.

```ruby
2.3.3 :002 > "hi".class
 => String
2.3.3 :002 > "there".class
 => String
```

We expect that if a `String` can do something, any `String` can do that similar
thing, that's a core part of what makes similar things similar in our human
brains.

For example, in Ruby, `String`s know how long they are. We'll explain what's
going on specifically in the next section, but:

```ruby
2.3.3 :003 > "hi".length
 => 2
2.3.3 :004 > x = "hi"
 => "hi"
2.3.3 :005 > x.length
 => 2
2.3.3 :006 > y = "there"
 => "there"
2.3.3 :007 > y.length
 => 5
2.3.3 :008 > tip = "These two strings need at least #{ x.length + y.length } slots"
 => "These two strings need at least 7 slots"
2.3.3 :009 > puts tip
These two strings need at least 7 slots
 => nil
```

Amazing, right? Instances being smart about themselves means you can ask them
what they know about themselves and don't have to do the work yourself! Ruby's
default classes (`String`, `Integer` and many others!) can do a lot of work for
you so that you can focus on your dreams instead of writing "external" methods
to count `String` length.

## Define Attribute / Property

An attribute on an instance is a fixed bit of information that the instance can
provide you. In Ruby, all instances have an attribute called `.class`. `String`s
in Ruby also have the attribute or property called `length`.

```ruby
2.3.3 :003 > "hi".length
 => 2
2.3.3 :004 > x = "hi"
 => "hi"
2.3.3 :005 > x.length
 => 2
```

`Integer`s _do not_ have the `length` attribute.

```ruby
2.3.3 :010 > 3.14.length
NoMethodError: undefined method 'length' for 3.14:Float
```

Just as fish don't have a "knit" method, `Float`s don't know how long they are.

Attributes are tiny little facts that an object knows about itself that it
***returns*** when asked.

## Define "Dot-notation" Syntax

We access an attribute by adding a `.` and then the `attribute name` after the
instance or a variable pointing to the instance. We discovered `"hi"`'s class by
asking it for its `.class` attribute.

## Define Method

Ruby instances have "internal" methods. You didn't define them by writing
`def...end` somewhere. The makers of Ruby did! While attributes report simple
facts, methods are activities that instances know how to do. In Ruby, a
`String` knows how to **_return_** a `reverse`d or `capitalize`d version of
itself.

```ruby
2.3.3 :011 > mirror = "olleh"
 => "olleh"
2.3.3 :012 > mirror.reverse
 => "hello"
2.3.3 :014 > mirror.capitalize
 => "Olleh"
```

Just as before, an `Integer` does not know how to `.reverse`:

```ruby
2.3.3 :013 > 2112.reverse
NoMethodError: undefined method `reverse' for 2112:...
```

**_What methods or attributes an instance has available depends on its class._**

## Demonstrate Method Chaining

Here are three facts:

* Values return values (themselves!)
* Attributes return values
* Methods return values

And we agree that values (or instances, or objects) can have methods or
attribute requests made upon them by using "dot-notation."

Let's imagine (or try out in IRB!) we evaluate this expression:

```ruby
2.3.3 :011 > mirror = "olleh"
 => "olleh"
```

The variable `mirror` points to a value of class type `String`. We can invoke a
method on it to reverse the order of letters:

```ruby
2.3.3 :017 > mirror.reverse
 => "hello"
```

Or we could capitalize the value pointed at by `mirror`:

```ruby
2.3.3 :017 > mirror.capitalize
 => "Olleh"
```

But the _return value_ of `capitalize` is a `String`, just like the original
`String` of `"olleh"`. So we should be able to invoke a `String` method on the
return value of `capitalize`. Indeed, we can:

```ruby
2.3.3 :017 > mirror.reverse.capitalize
 => "Hello"
```

As a sneak peek of what this means, we will be able to do things like:

```ruby
first_place = sales_team.sort.first
puts "#{first_place.name} gets coffee; coffee is for closers"
```

Method chaining allows us to express powerful ideas with very little typing. In
some ways, this idea is now surpassing conversation: it's allowing us to
express complex human ideas in tiny words separated by `.`. Amazing!

## Find Documentation About Methods and Attributes

We know you're really excited about `reverse` and `capitalize`. There yet other
attributes and methods supported by `String`. We can look in the Ruby
documentation for [`String`][string]. Or you could look at the information for
[`Integer`][integer] or `Float`. Check it out and try it out!  We just found
the _method_ `.count` which takes as an _argument_ another `String` to search
for:

```ruby
2.3.3 :018 > "zaboomafoo".count("o")
 => 4
```

Feel free to explore! If a _method_ seems weird, it's OK to skip it. Try
ones that seem obvious or interesting. Here's a fun one:

```ruby
# Convert an Integer to a String, use String's count method to count
# the 0's present. Use that number as the first term in a ternary expression
# and puts the result. Amazing!

puts 100000000.to_s.count("0") > 6 ? "Big Money!" : "Chump Change"
Big Money!
```

## Conclusion

instances to tell us about their _attributes_ or to return transformations of
themselves through _methods_. Instances are linked by their class and Ruby's
documentation on classes tells you what attributes and methods instances of
that class respond to. If you ask an instance to do something that its class
doesn't make available, Ruby will report an error.

## Resources

- [`String` Documentation][string]
- [`Integer` Documentation][integer]

[string]: https://ruby-doc.org/core-2.6.3/String.html
[integer]: https://ruby-doc.org/core-2.6.3/Integer.html
[float]: https://ruby-doc.org/core-2.6.3/Float.html
