---
title: Assignment 4 - More with Lists & Recursion
geometry: margin=3cm
draft: false
---

This assignment departs from the textbook, so there's nothing to read. I think this content is really cool, but it might be too hard to include in the actual class. And it may especially be too hard for you all since I can't do a lecture! If so, feel free to skip or just let me know.


From now on, you may use the following _syntactic sugar_ for lists that you already saw in the textbook:

    [list: 1, 2, 3] = link(1, link(2, link(3, empty)))

(Pyret converts the former into the latter before running it, so it's just for ease of writing examples and tests.)

    [list: ] = empty

as well.

## Higher-order functions

Create a file called `higher-order-functions.arr`.

### Map

Recall the function (from the textbook) to double every number in a list:

    fun my-doubles(l):
      cases (List) l:
        | empty => empty
        | link(f, r) => link(2 * f, my-doubles(l))
      end
    end

This bears a striking resemblence to the function you wrote to add an exclamation mark to every string in a list:

    fun exclaim(l):
      cases (List) l:
        | empty => empty
        | link(f, r) => link(f + "!", exclaim(l))
      end
    end

In both cases, we recur through a list and apply some function to each element in the list.

Fortunately, we can write what's called a _higher-order_ function: a function that takes another function as one of its arguments! This works just the same as passing any other argument to the function.


1. Write the higher-order function `my-map` that takes as input a list `l` and a function `func`, and produces a list made from applying `func` to every element in `l`. (This is called _mapping_ the function `func` across the list `l`.) Start with:

````
    fun my-map(func, l):
      ...
    end
````

Within the body of the function, you'll be able to call `func` like any other function.


2. Rewrite `my-doubles` and `exclaim` using `my-map`. You will need to write helper functions to use as `func` in each case. (That is, you'll need to write a function `double-one` and `exclaim-one` that double a single number, and add an exclamation point to a single string, respectively.)

    You do not need to directly test `my-map`: the examples you write for `my-doubles` and `exclaim` suffice to test it. 


### Anonymous functions

Writing helper functions to use as inputs for `my-doubles` makes using high-order functions more verbose. Fortunately, we can create functions _anonymously_ to use as arguments to our higher-order functions.

An anonymous function looks like this:

    lam(x): x + 1 end

or

    lam(x, y): x + y end


The `lam` is short for "lambda", as in [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus). (If you look closely at the Pyret mascot you'll be able to spot a lambda symbol: λ.)

__Optional:__ refactor `my-doubles` and `exclaim` from (2.) using anonymous functions.

For example, to add 1 to every element in a list:

```
    my-map(lam(x): x + 1 end, [list: 1, 2, 3])
    => [list: 2, 3, 4]
```

### Fold

Now consider the function `my-sum`, which adds up all the numbers in a list:

    fun my-sum(l):
      cases (List) l:
        | empty => 0
        | link(f, r) => f + my-sum(r)
      end
    end


We could write a similar function, `my-multiply`, to multiply together all the numbers in a list:

    fun my-multiply(l):
      cases (List) l:
        | empty => 1
        | link(f, r) => f * my-multiply(r)
      end
    end

Let's think about what's going on in these functions.

Each function returns some specific value if it sees an empty list. Otherwise, it has a way to combine an element from the list with the result of the recursive call on the rest of the list.

In short, the body of each function looks like this:

    cases (List) l:
      | empty => [base case]
      | link(f, r) => [do something with f and the recursive call on r]
    end

This recursive combination is called a _fold_.


3. Write the higher-order function `my-fold` that takes as input a two-argument "combining" function `func`, a value `base-value` and a list `l`. If `l` is empty, `my-fold` evaluates to `base-value`, otherwise `my-fold` produces a new value by repeatedly applying `func`.

4. Use `my-fold` to rewrite `my-length` (finds the length of a list), `my-sum` and `my-multiply`. You may use anonymous functions or helper functions.


_`map` and `fold` are built in to Pyret, and after you implement them yourself you are free to use the built-in versions for future problems and assignments._

## Harder list functions

Create a file called `lists2.arr`

5. Write a function `my-reverse` that consumes a list `l` and produces a new list with the same elements in reverse order.

6. Write a function `my-concat` that consumes two lists `l-1` and `l-2`, and produces a list with all the elements from `l-1` followed by all the elements from `l-2`.

_After you implement `my-reverse` you are welcome to use the built in `reverse`. After you implement `my-concat`, you can concatenate lists in Pyret by using the `+` operator, for example,_

```
[list: 1, 2, 3] + [list: 4, 5]
=> [list: 1, 2, 3, 4, 5]
```


__Optional challenge:__ Write a function `subsets` that consumes a list `l`, and produces a _list of lists_ where each list contains the elements of a single subset of `l`. For example, `subsets` should produce the following (subject to reordering):

```
    subsets([list: ])
    => [list: [list: ]]
    
    subsets([list: 1])
    => [list: [list: 1], [list: ]]
    
    subsets([list: 1, 2])
    => [list: [list: 1, 2], [list: 1], [list: 2], [list: ]]
```

This problem is notoriously tough, scroll all the way down if you'd like any hints.

## Turn in

Download `higher-order-functions.arr` and `lists2.arr` and submit them to gradescope.


.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.
#### Subset hint. 1

Lets think about the list `[list: 1, 2]` and its 4 subsets:
```
[list: 1, 2], [list: 1], [list: 2], [list: ]
```
or
```
{1, 2}, {1}, {2}, {}
```

The subsets are made by considering each element of the original list, and either _including it_ or _not including it_ in the subset. So our program needs to figure out how to do the following:

````
          include 1?
           /     \
         yes     no
        /          \
    incude 2?      include 2?
      /  \          /  \
    yes   no      yes   no
   /       \      /      \
{1, 2}     {1}  {2}      {}
````


.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.
#### Subset hint. 2
Thinking recursively, we can break each step down like this:

```
          include 1?
          /        \
        yes         no
        /            \
   add 1 to          subsets of          
  subsets of          [list: 2]
  [list: 2]           
```



.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.\
.
#### Subset hint. 3
To add `1` to the recursive subsets call, `map` `lam(x): link(1, x) end` over the recursive call.
