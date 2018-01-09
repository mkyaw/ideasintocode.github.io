---
layout: post
title:  "Get Your Feet Wet With Object Oriented Programming in PHP"
date:   2018-01-08 08:18:00
categories: PHP
---

Object Oriented Programming, as the name suggests, is all about objects. 

You are basically trying to create a piece of software neatly organized in objects. This approach makes the code scalable with reusable components.

#### Man Class

Let's say you want to create a program about men in general. I apologize in advance for all the stereotyping ( should I though? X) )


Average men have all kinds of stuff in common like giving firm handshakes, being stubborn, not putting toilet paper rolls back, falling in love with the latest gadgets, etc. These could be described as behaviors or methods of Man object.

Men also have their own distinct features like age, height, favorite sports, favorite drinks, etc. These could be described as properties or attributes of Man object.

With these in mind, creating a Man class is not so difficult anymore. So, the program would go like this.

{% highlight php %}
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

#### Man Object

Now that we have this Man class, we can create any particular man by creating an instance of class known as class instantiation.

{% highlight php %}
<?php

// Create a Man object called "Jack" (i.e. instantiation)
$jack = new Man();

// Set values to Jack's attributes
$jack->name = "Jack";
$jack->age = 30;
$jack->height = "6 feet";
$jack->fav_sports = ["basketball", "soccer"];
$jack->fav_drinks = ["coffee", "green tea"];

// Print out Jack's attributes and values
echo "Our man's name is: " . $jack->name . "\n";
echo "He is " . $jack->age . " years old and " . $jack->height . " tall.";

echo "His favorite sports are: ";
foreach ($jack->fav_sports as $sport) {
    echo $sport . " ";
}

echo "\nHis favorite drinks are: ";
foreach ($jack->fav_drinks as $drink) {
    echo $drink . " ";
}

// Print out Jack's behaviors common to all men (hint: defined in Man class)
echo "\nHe said these are some of his behaviors common to other men: ";
echo "\n\t" . $jack->giveFirmHandshakes();
echo "\n\t" . $jack->beStubborn();
echo "\n\t" . $jack->notPutToiletPaper();
{% endhighlight %}

Here you can see that a man named Jack was created with name of “Jack”, height of “6 feet”, favorite sports “basketball and soccer” and favorite drinks “coffee and green tea”. These attributes are called instance variables.

Then he has the behaviors of all the men like giving firm hand shakes, being stubborn and not putting back toilet paper. All these behaviors are called instance methods.

#### Constructors

So far, we created a class called “Man” and an object called “Jack” by instantiating that class. We also gave Jack values for his attributes (name, height, favorite sports and drinks) and call his behaviors common to all men (giving firm handshakes, staying stubborn and not putting toilet papers back).

Let's take this idea one step further and get Jack to start introducing himself whenever we create Jack object without actually having to print them out individually like this:

{% highlight php %}
// Print out Jack's attributes and values
echo "Our man's name is: " . $jack->name . "\n";
echo "He is " . $jack->age . " years old and " . $jack->height . " tall.";
{% endhighlight %}

This is where constructors come into play. Constructors are basically special methods that get called when an object is created.

So, the idea is to print out Jack's name, age and height when we create “Jack” object by instantiating Man class. In order to make this happen, we need to however specify the name, age and height when we create the object like this:

{% highlight php %}
// Create a Man object called "Jack"
$jack = new Man('Jack', 30, '6 feet');
{% endhighlight %}

This code tells the Man class to create an object with 3 parameters: 'Jack' for name, 30 for age and '6 feet' for height.

Now that we have passed these parameters while instantiating the class, we can easily use them to create the constructor method.

{% highlight php %}
// Create a constructor method with 3 required parameters: name, age and height
public function __construct($name, $age, $height)
{
    echo "object created\n";
    
    // Assign the values of parameters to properties 
    // Also known as instance variables
    // Using "$this->property_name"
    $this->name = $name;
    $this->age = $age;
    $this->height = $height;
    
    // Print out Jack's attributes and values
    echo "Our man's name is: " . $this->name . "\n";
    echo "He is " . $this->age . " years old and " . $this->height . " tall.";
}
{% endhighlight %}

So, now whenever we instantiate Man class, we need to put 3 parameters and they will be printed out right away.

{% highlight php %}
// Create a Man object called "Jack"
$jack = new Man('Jack', 30, '6 feet');

// Output:
// => Object created
// => Our man's name is: Jack
// => He is 30 years old and 6 feet tall.
{% endhighlight %}

The complete code with constructor would be something like this:

{% highlight php %}
<?php
 
class Man
{
    // 1. Declare the properties
    public $name;
    public $age;
    public $height;
    public $fav_sports;
    public $fav_drinks;
    
    // 2. Create a constructor method with 3 required parameters: name, age and height
    public function __construct($name, $age, $height)
    {
        // 2A. Assign the values of parameters to class properties
        // Also known as instance variables
        // Using "$this->property_name"
        $this->name = $name;
        $this->age = $age;
        $this->height = $height;
        
        // 2B. Print out Jack's attributes and values
        echo "Our man's name is: " . $this->name . "\n";
        echo "He is " . $this->age . " years old and " . $this->height . " tall.";
    }
 
    // 3. Create methods
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

// 4. Create a Man object called "Jack"
// This will print out the echo statements inside "__construct" method inside the class
$jack = new Man('Jack', 30, '6 feet');
 
// 5. Set values to Jack's favorite sports and drinks
$jack->fav_sports = ["basketball", "soccer"];
$jack->fav_drinks = ["coffee", "green tea"];
 
// Print out Jack's favorite sports and drinks
echo "His favorite sports are: ";
foreach ($jack->fav_sports as $sport) {
    echo $sport . " ";
}
 
echo "\nHis favorite drinks are: ";
foreach ($jack->fav_drinks as $drink) {
    echo $drink . " ";
}
 
// Print out Jack's behaviors common to all men
// (hint: defined in Man class)
echo "\nHe said these are some of his behaviors common to other men: ";
echo "\n\t" . $jack->giveFirmHandshakes();
echo "\n\t" . $jack->beStubborn();
echo "\n\t" . $jack->notPutToiletPaper();
{% endhighlight %}

Now, we don't have to set Jack's name, age and height separately and print them anymore. 

Whenever we create Jack object, we just specify his properties as the parameters and they will get printed automatically by the help of the constructor. We can also put his favorite sports and drinks in the parameter if we want by specifying them as parameters while creating the object and putting the echo lines inside the constructor.

You can visit [here](http://php.net/manual/en/language.oop5.decon.php){:target="_blank"} for more information on PHP implementation of constructors. Our OOP journey has been slow but steady.