---
title: Assignment 3 - Tables & Lists
geometry: margin=3cm
draft: false
---

## Tables

Read [§4.1 in DCIC](https://dcic-world.org/2023-02-21/intro-tabular-data.html).

### Table Problems

Create a file called `tables.arr`.

Include the following table definitions (from the textbook) in your definitions panel:

    people = table: name, age
      row: "Alicia", 30
      row: "Meihui", 40
      row: "Jamal", 25
    end

    shuttle = table: month, riders
      row: "Jan", 1123
      row: "Feb", 1045
      row: "Mar", 1087
      row: "Apr", 999
    end

1. Write function `is-winter` that takes a Row `r` with a "month" column as input and produces a Boolean indicating whether the month in that row is one of "Jan", "Feb", or "Mar".

2. Write function `low-winter` that takes a Row `r` with both "month" and "riders" columns and produces a Boolean indicating whether the row is a winter row with fewer than 1050 riders.

3. Write function `oldest` that takes a Table with columns "name" and "age", and produces the "name" of the "row" with the largest "age".


## Lists

You should reference [§5.2 in DCIC](https://dcic-world.org/2023-02-21/processing-lists.html) for techniques to solve the problems in this section, but you'll just need to know and use the following.

__Lists__ are a data type that take one of two forms:

- `empty`, or
- `link(first, rest)`.

The list `empty` is just that: a list with nothing in it. A list made with `link(first, rest)` contains two parts: `first` is any value (a number, string, boolean, etc) and `rest` is a list.

So for example, a list of the numbers 1, 2, and 3 in Pyret is written as,

`link(1, link(2, link(3, empty)))`.

(The textbook introduces a shorthand way to write lists that looks like `[list: 1, 2, 3], which we will use in the future but you should ignore for now.)

Given a list, you can process it using a __cases expression__:

    cases (List) l:
      | empty => [ expression 1 ]
      | link(f, r) => [ expression 2 ]
    end

If the list `l` is the empty list, the outer expression will evaluate to expression 1. If `l` is not the empty list, the cases expression will evaluate to expression 2, in which the values `f` and `r` are available.

So for example, the following expression will evaluate to one of two strings depending on whether `l` is empty.

    cases (List) l:
      | empty => "this list is empty"
      | link(f, r) => "this list is not empty"
    end

To deal with the recursive nature of lists (a list which is not empty contains another list), you can use ___function_ recursion__ by calling a function from within that function itself.

For example, the following function will compute the length of a list.

    fun my-len(l :: List) -> Number:
      cases (List) l:
        | empty => 0
        | link(f, r) => 1 + my-len(r)
      end
    end

If we called this function on our example list `link(1, link(2, link(3, empty)))` the evaluation would proceed like this:

    my-len(link(1, link(2, link(3, empty))))
    => 1 + my-len(link(2, link(3, empty)))
    => 1 + 1 + my-len(link(3, empty))
    => 1 + 1 + 1 + my-len(empty)
    => 1 + 1 + 1 + 0
    => 3

### List problems

Create a file called `lists.arr`.

1. Write function `my-sum` that takes as input a list of numbers and evaluates to the sum of the numbers of the list.

2. Write function `exclaim` that takes a list of strings, and adds "!" to the end of them. (To concatenate two strings together, use the `+` operator. For example, `"hi" + "!"` evaluates to `"hi!"`.)

3. Write function `first-n` that takes a list `l` and a number `n`, and evaluates to a list made of only the first `n` elements of `l` (or the whole list `l` if `n` is greater than the length of `l`.)

4. Write function `insert-nth` that takes a list `l`, a number `n` and a value `e`, and evaluates to the list `l` with element `e` inserted after the first `n` elements (or at the end, if there are fewer than `n` elements in `l`).

5. Write function `find-element` that takes a list `l` and an element `e` that is in `l`, and evaluates to the first position at which `e` occurs in the list `l`. For example, `find-element(link(1, link(2, link(3, empty))), 2) = 1`. If the element doesn't exist in the list, you may return whatever value you'd like or `raise` an error.

	_Hint: you may want to write a helper function with an acculumating index._

## Turn in

Make sure that all your functions include a docstring and a sufficient number of test cases.

Download your files `tables.arr` and `lists.arr` and email them to me.
