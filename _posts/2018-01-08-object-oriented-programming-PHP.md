---
layout: post
title:  "Get Your Feet Wet With Object Oriented Programming in PHP"
date:   2018-01-08 08:18:00
categories: OOP, PHP
---

Object Oriented Programming, as the name suggests, is all about objects. 

You are basically trying to create a piece of software neatly organized in objects. This approach makes the code scalable with reusable components.

### Man Class

Let’s say you want to create a program about men in general.


Average men have all kinds of stuff in common like giving firm handshakes, being stubborn, not putting toilet paper rolls back, falling in love with the latest gadgets, etc. These could be described as behaviors or methods of Man object.

Men also have their own distinct features like age, height, favorite sports, favorite drinks, etc. These could be described as properties or attributes of Man object.

With these in mind, creating a Man class is not so difficult anymore. So, the program would go like this.

{%highlight php %}
<?php

class Man
{
    public $name;
    public $age;
    public $height;
    public $fav_sports;
    public $fav_drinks;
 
    public function giveFirmHandshakes()
    {
        return "I give firm handshakes.";
    }
 
    public function beStubborn()
    {
        return "I am stubborn.";
    }

    public function notPutToiletPaper()
    {
        return "It's not humanly possible to remember to put toilet paper rolls when they are finished";
    }
}
{% endhighlight %}