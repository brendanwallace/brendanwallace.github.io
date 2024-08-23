---
title: Assignment 2 - Functions & Conditionals
geometry: margin=3cm
draft: false
---

## Instructions

Read DCIC section §3.3 & §3.4 <https://dcic-world.org/>. The main ideas are:
	
- conditions & booleans
- repeated expressions to functions
- docstrings, testing and the design contract
	
So far, we've encountered _values_, such as a particular images, numbers or strings; and _expressions_, which are combinations of operations and values that _evaluate to_ single values.
	
For all of the problems in this assignment (and for most of the rest of the assignments), your task will be to write one or more _functions_, programming constructs that allows you to reuse expressions with different inputs (called parameters) to solve particular problems.


## Problems

### Warmup
	
1. Create a Pyret file called `flags2.arr`. Write a function called `vietnam-custom` that takes two parameters `first-color` and `second-color`, and evaluates to the Vietnam flag if those parameters are "red" and "yellow", or to an identically structured flag with different colors otherwise.

	Add a second function `chile-custom` that does the same thing for the Chilean flag. (You do not need to include `doc-string`s or `where` blocks for these functions.)

	_Optional: include your favorite custom-color redesign of one of these flags._ 


### Functions with `doc-string`s and `where` blocks

For the remainder of these problems, include a `doc-string` explaining briefly what the function does, and 2-6 `examples` in a `where` block.

2. Create a Pyret file called `weightlifting.arr`. Write a function called `bar-weight` that takes arguments `num-plates`, and evaluates to the weight _in pounds_ of a 20kg bar with `num-plates` number of 20kg plates. Use an approximate conversion such that one kg is 2.2 pounds, and check that an empty bar weighs 44 pounds, and a bar with two plates weighs 132 pounds.


3. In `weightlifting.arr`, add a function called `bar-weight-custom` that takes arguments `bar` of "w" or "m" for a women's 15kg or a men's 20kg bar respectively, and `num-plates` number of 20kg plates, and evaluates to the number of pounds the bar weighs.


4. Create a Pyret file called `cookies.arr`. Write a function called `is-cookie-good` that takes arguments `flour`, `sugar`, `butter`, and `nuts` (all measured in cups) and evaluates to a boolean of whether a cookie made using that amount (in cups) of ingredients is good.

	How can you tell whether a cookie is good? For starters, there should be more flour than sugar and butter combined (or it will fall apart). Next, consider the ratios of nuts to butter ("crunchiness"), sugar to flour ("sweetness"), and butter to sugar ("savoriness"). To be good, a cookie requires sweetness of at least 1/3, savoriness at least 2, and crunchiness at least 1/2.
	
	To test your function, make sure a cookie in the 3:2:1 ratio (3 cups flour, 2 cups butter, 1 cup sugar) with 1 cup of nuts is good. Make sure that a common cake recipe with 2 cups of flour, butter and sugar each (with no nuts) is *not* a good cookie.



## Turn in

Download your files `flags2.arr`, `weightlifting.arr` and `cookies.arr` files and email them to me.