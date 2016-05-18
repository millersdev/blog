---
layout: post
title: Naming colors in Sass
date: 2016-05-18
summary: This article explains how to make colors in CSS more fun
categories: 
  - css
  - sass
---
Using colors in your CSS is often a real challenge. In this article I'm going to explain how you can make this a lot more fun.

##  The problem

Let's say you have the following CSS:

{% highlight css %}
h1 {
	color: #4682B4;
}

a {
	color: #4682B4;
}

.blue-bar {
	background-color: #4682B4;
}
{% endhighlight %}
	
You see that the same color is used multiple times. If you decide to change the color, you have to change it in three different places. In large projects, this will be a lot more and it will be a real nightmare.

## The solution

When you're using [Sass](http://sass-lang.com/), you can use variables for this. You create a variable for each color, and you use the variable wherever you want to use that particular color.

{% highlight scss %}
$blue: #4682B4;

h1 {
	color: $blue;
}

a {
	color: $blue;
}

.blue-bar {
	background-color: $blue;
}
{% endhighlight %}
	
In this case you have only one color. But what are you going to do when you decide to add new shades of that same color? You have to give them all unique names, so you might end up with something like this:

{% highlight scss %}
$blue1: #4682B4;
$blue2: #4682B4;
$blue3: #4682B4;
$blue4: #4682B4;
{% endhighlight %}
	
This might work if you have only two or three shades of the same color, but how are you going to keep track of which variable is which shade of blue when you have a whole bunch of them? You have to give them a better name.

{% highlight scss %}
$blue: #4682B4;
$lighter-blue: #4682B4;
$darker-blue: #4682B4;
$really-dark-blue: #4682B4;
{% endhighlight %}
	
This looks a lot better, but is `$lighter-blue` the color that you used for the background, or was that `$blue`? These names don't give much information. They don't tell you anything about where the color is used. And what happens when you add another shade of blue that is lighter than `$lighter-blue`? Are you going to add an `$even-lighter-blue`? You don't want to do that. A much better approach is to take a look at a tool that gives colors a more colorful name, e.g. [Name That Color](http://chir.ag/projects/name-that-color/#6195ED). Just type in your hexcode, and it gives you a nice name that you can use in your code. You then end up with something like this:

{% highlight scss %}
$cornflower-blue: #6195ED;
$steel-blue: #4682B4;
$spring-green: #12FE57;
{% endhighlight %}
	
It gives you a better idea of what kind of color it is, although the real problem still isn't solved. This list of colors still doesn't tell you where these colors are used. If you change one of the colors, it won't give you any clue about which elements on the website will be touched. The solution is quite easy. Just add another list of variables that gives you this information.

{% highlight scss %}
$cornflower-blue: #6195ED;
$steel-blue: #4682B4;
$spring-green: #12FE57;

$header-text-color: $cornflower-blue;
$header-background-color: $spring-green;
$default-text-color: $steel-blue;
{% endhighlight %}
	
If you want to change the background color of your header, just assign a different color variable to the `$header-background-color`. That's it. I hope this makes colors in CSS more fun!