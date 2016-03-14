+++
categories = ["DEVELOPMENT"]
date = "2016-03-14T01:43:44-07:00"
description = "Fluent:Interfaces :: Infix:Notations"
draft = false
image = "/img/fluent-wins.jpg"
tags = ["coding", "code-style", "lazy-coder"]
title = "Why Fluent Wins"
+++

> Fluent APIs better match our mental model of how data is processed == WIN 

# Cześć (hello in Polish)
Does this make sense to you?  

`+ 3 4 `

You may read this as It roughly reads like "Let's do an addition of 3 and 4."  Sure, you may be familiar with ["Polish Notation"](https://en.wikipedia.org/wiki/Polish_notation) or variants like "Reverse Polish Notation" or RPN, but it's not how most people naturally process these kind of operations.  

Of course we usually think about it like this:

`3 + 4`

Here we envision this as "You have three, now add to it four" this seems natural.  And as we'll see, this is aggravated when you chain many operations.

# Functions make us think in reverse

Functions/Methods act more like Polish notation:

`int result = Math.pow(2,3); // 8`

So when programming we write `POWER 2,3` while in math terms we would write `2^3`.  This gets even more confusing when you chain several operations.  Let's take the example of doing some data conversion.  Examine this sample process of doing some data transformation:

1. Get a string from an XML document
2. [Base64](https://en.wikipedia.org/wiki/Base64) decode the string to get the binary value
3. Decrypt the binary value
4. Encode the clear binary value as an ASCII string

Let's look at how this process would be carried out using normal function 

````
var result = ASCIIEncode( Decrypt( Base64Decode( xml.GetAttribute("foo") ), decryptParameters ) );
````

When reading this code, the order is almost completely reversed.  Also, when writing it, we keep having to jump around to "surround" one function with another, watch:

![traditional functions](/img/fluent-bad.gif)

Of course, this can be partially remedied with intermediate variables, but you may not have any use for them.

One style of API that remedies this is the [Fluent Interface](http://martinfowler.com/bliki/FluentInterface.html)

# Fluent Methods go step by step

A fluent interface usually works by always returning an object of a shared type which exposes common functions.  [jQuery](https://jquery.com/) is a prime example:

```
$(".some-class")
  .css("color","red")
  .css("padding",10)
  .on("click", function(){ console.log("hai"); });
```

Another way is simply by adding methods which are commonly exposed only as functions on the types they operate on, for example:

Instead of a generic utility class like:
```
public class Math
{
    // ...
    public Double Power(double base, double exponent)
    {
        // ... 
    }
}
```

Imagine a method on the numeric type itself like:
```
public class Double
{
    // ...
    public Double ToPower(double exponent)
    {
        return pow(this,exponent); 
    }
}
```
With usage like `2.ToPower(3)` Clearer, isn't it?  

There are some side benefits as well.  For example, there's less chance you could confuse **parameter order** with this version of the power function.  This also gives us a very **guided way to organize methods**.  Instead of having a generic 'utility' class, we add methods to whichever class they apply.  This makes it easier for future developers to find where to find add new utility methods and can help avoid [Bikeshedding](https://css-tricks.com/what-is-bikeshedding/) about how to organize APIs.

# Example, Fluent-ized
Let's return to our data conversion sample from earlier, and assume we've added on the needed class methods for the conversions.

```
var result = xml.GetAttribute("foo").FromBase64().Decrypt(decryptParameters).ToASCII();
```

See how much easier it is to follow?  You can read through the conversion left to right and typing is much smoother as well, watch:

![fluent interface](/img/fluent-good.gif)

You could say this style of API is more "ergonomic" for the consumer.  You can achieve this in C# using [Extension ](https://msdn.microsoft.com/en-us/library/bb383977.aspx) [Methods](http://www.dotnetperls.com/extension), which I'll have to write about soon :)

**Use Fluent API design whenever possible to ease your consumer's development** 

(P.S. Thanks to [Livetyping](http://text.livetyping.com/) for the typing animations!)