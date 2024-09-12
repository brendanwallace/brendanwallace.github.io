---
title: Assignment 5 - Structured Data
geometry: margin=3cm
draft: false
---


## Structured & conditional data

Read [§6.1 in DCIC](https://dcic-world.org/2023-02-21/intro-struct-data.html).

### Revisiting bar weights

We're going to rewrite and expand our `bar-weight` function from an earlier assignment using structured data. Start by creating a file `weightlifting2.arr`.


1. Create a variable data type `Bar`, that can be `womens-olympic`, `mens-olympic`, `trap`, `squat-safety`, or `swiss`.

2. Write a function `bar-weight` that consumes a single variable `bar` of type `Bar` and produces the weight of that bar in kg, using the following:

|bar    | weight (kgs)|
|:-----| :---------: |
| womens-olympic| 15|
| mens-olymic | 20 |
| trap | 25 |
| squat-safety| 32 |
| swiss | 11.4 |

3. Create a variable data type `Plate`, that can be `red`, `blue`, `yellow`, `green`, `white`, `black`, or `custom(weight :: Number)` (a custom weight).

4. Write a function `plate-weight` that consumes a single variable `plate` of type `Plate` and produces the weight of that plate in kg, using the following:

|plate| weight (kgs)|
|:----|:-----:|
| red |   25  |
|blue |   20  |
|yellow| 15   |
| green | 10  |
| white | 5   |
| black | 2.5 |
| custom|(variable)| 


5. Write a function `weight-in-pounds` that consumes a `Bar` and a list of `Plates` and produces the weight _in pounds_ of that bar loaded with that list of plates, using the conversion rate of 1 kg = 2.2 pounds.

The type signature should be the following:

```fun weight-in-pounds(bar :: Bar, plates :: List<Plate>) -> Number```

__Optional challenge 1.__[^1] Write a function `choose-plates` that determines the plates to add to a bar to achieve a certain weight in kilograms. 

```fun choose-plates(bar :: Bar, weight-kg :: Number) -> List<Plate>```

Your program should add plates _in pairs_, and should always prefer the heaviest available plates, ending with custom plates only if no other plates can be added.

[^1]: This turns out to be quite difficult, so only do it if you have extra time or really want the challenge. You'll need to break the problem into subproblems and write a couple helper functions along the way.

### Recursive data & Trees

The data definition for a `List` looks like this:

```
data List:
  | empty
  | link(first :: Any, rest :: List)
end
```

This is _recursive_: one of the fields of a `List` is itself a `List`.


Now consider the definition of a "tree":

```
data Tree<V>:
  | leaf
  | branch(value :: V, left :: Tree<V>, right :: Tree<V>)
end
```

This is just like a `List`, but instead of having one recursive `rest` it has two recursive parts, a `left` and `right` that are both `Trees`.

Here's an example of a tree.
```
         1
        / \
       2   3
      / \
     4   5
```

To represent this in our code, we would write:

```
branch(1,
	branch(2,
		branch(4, leaf, leaf),
		branch(5, leaf, leaf)),
	branch(3, leaf, leaf))
```

We can write a function that counts the number of elements in a tree as follows.

```
fun tree-size(t :: Tree) -> Number:
  doc: "counts the number of elements in a tree"
  cases (Tree) t:
    | leaf => 0
    | branch(v, l, r) => 1 + tree-size(l) + tree-size(r)
  end
where:
  tree-size(leaf) is 0
  tree-size(branch("hi", branch("hello", leaf, leaf), leaf)) is 2
end
```

Create a file called `trees.arr`.

1. Write a function `tree-sum` that sums all the values in a tree of numbers.

2. Write a function `tree-height` that finds the height of a tree. The height of a tree is the longest path that exists from the root (first element) of the tree to any one non-leaf node, or zero if the tree is a `leaf`. For example, the height of our example tree above is 3.

3. Write a function `tree-equal` that determines whether two trees are equal.

__Optional challenge 2.__[^2] Write a function `is-tree-subtree` that determines whether one tree is a _subtree_ of another tree. A tree is a subtree of another if the first appears somewhere in the other. For example, the following are all subtrees of the example tree above:

```
   1          2        1        1      (leaf)
  / \        / \        \       
 2   3      4   5        3       
```

(A tree is also a subtree of itself.)

[^2]: Again, this is is quite hard. But if you're having fun with trees and want one more problem please have at it! If you need a hint: write a helper function `subtree-at-root` that determines whether one tree appears as a subtree _at the root_ (top position) of another tree. Your `is-tree-subtree` then makes use of this function recursively.



## Turn in

Download `weightlifting2.arr` and `trees.arr` and submit them to gradescope.