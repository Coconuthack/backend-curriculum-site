---
title: Beginner Enumerables
length: 120
tags: enumerables, map, select, find, each
---

## Learning Goals

* Learn how to use & recreate the functionality of `.map`, `.select` and `.find` using `.each`
* Understand when to use `.map`, `.select` and `.find` appropriately.
* Learn how to explore new enumerables using Ruby docs.


## Vocabulary  
* enumerable  
* iterate  
* map, find, find_all
* return value

## Warm Up  
* What is **iteration** and when do we use it?
* In your notebook, write the block of code to use `.each` to print each letter in the following array `dynasty_1 = ["K", "e", "n", "n", "e", "d", "y"]`
* In your notebook, write the block of code to use `.each` to create an array of the following names, in all caps: `names = ['Jack', 'Bobby', 'Teddy']`

## Intro

Earlier this week, we learned about the method \#each. We used \#each to iterate over a collection to accomplish a variety of tasks: transforming collections, pulling a subset of elements, and creating new things based on some or all of the elements in the collection.  Because iteration is something we do on a nearly daily basis as programmers, Ruby has built some out-of-the-box tools that help us streamline the more common iteration patterns.  These tools are categorized as **enumerables**.  Enumerables are methods that take the base function of \#each and build on it to simplify certain patterns of iteration.

Before we get into the enumerables themselves, let's take a moment to form a strategy for learning all of these new methods.  Enumerables are one of the topics that we will cover that can be cemented in our minds through some simple flashcard exercises and memorization.  There are three key pieces of information that we will want to learn for each enumerable _and_ the method \#each:

  * syntax
  * return value
  * best use-cases

As we walk through some of the more common enumerables, we will be making flashcards for each - you will be able to use these flashcards as study tools to better cement each enumerable in your mind.

Let's start our flashcards with \#each.  The face of your index card should have the method name, \#each.  On the reverse side of the card, write the following information:

  * syntax:

    ```ruby
    collection.each do |element|
      # the block of code here will run for each element
    end
    ```
    
  * return value - \#each returns the original array
  * best use-cases - When iterating over a collection _and_ there is not an Enumerable that specifically accomplishes the goal.

By the end of the lesson, you will have a good stack of Enumerable flashcards that will help you learn when and how to use them as a better option than \#each.


### `map` / `collect`

`map` is a lot like `each`.

The difference is that `map` actually _returns whatever we do in the block_. Think about how this is different from each which will always return the content of the _original_ array.

Let's look at this in code. Taking an array of the numbers, we want to end up with an array with the doubles of each of those numbers. With `each`, we would do it like this:

```ruby
def double                    # define a method called double
  numbers = [1, 2, 3, 4, 5]   # declare a numbers variable with the value of an array

  result = []                 # declare a variable, results, with the value of an empty array

  numbers.each do |num|       # use `.each` to iterate over the numbers array
    result << num * 2         # shovel the current number x 2 into the result array
  end                         # end the `.each` method

  result                      # return the result array
end                           # end the double method

result
=> [2, 4, 6, 8, 10]           # our array of doubles

numbers
=> [1, 2, 3, 4, 5]            # numbers array, which is unchanged
```

We've written a method called `double`. We start off with `result`, which we set to an empty array. With each, we iterate through each item of `numbers`, and with each element, we are doubling the number and we are putting it into the `result` array. At the end, we are returning the `result` variable, which should now contain [2, 4, 6, 8, 10].

This code is decent. But there are things about it I'm not entirely thrilled about. For example, we are temporarily storing things in a variable, `result`, which is inefficient. You want to avoid the use of unnecessary variables when you can. This is how we can achieve the same result using `.map`.

```ruby
def double                # define a method called double
  numbers = [1, 2, 3, 4, 5]   # declare a numbers variable with the value of an array

  numbers.map do |num|    # iterate over numbers with `.map`
    num * 2               # number x 2
  end                     # end the `.map` method

end                       # end the double method

double
=> [2, 4, 6, 8, 10]       # our numbers array has been changed!
```

Instinctually, this should look better to you. We don't have any unnecessary variable assignment and `map` is handling all we need to return.

```ruby
def double
  numbers = [1, 2, 3 ,4, 5]

  numbers.map do |num|
    num * 2
    puts "I really love math"
  end

end
```

#### Discuss:
* With this code, what do you think this method returns? Why?  
* Many folks are tempted to save the result of map to a variable. Why might I disagree with this choice?  

#### Independent Practice
The method below returns an array of the brothers names in all caps; your job is to write one using the `map` method. (Touch an `enums_practice.rb` file in your M1 directory and write the code in that file)

```ruby
def kennedy_brothers
  brothers = ["Robert", "Ted", "Joseph", "John"]

  caps_brothers = []

  brothers.each do |brother|
    caps_brothers << brother.upcase
  end

  caps_brothers

end
```

**FlashCard**

Its time to create your next flashcard!  Using the same format that we used for \#each, create a flashcard for \#map - including syntax, return value, and use-cases.

**Turn & Talk**  
Share you flashcard with your neighbor.  Talk them through it and be specific. What is similar/different? Are there any changes/additions you want to make to your own flashcard?


### `find` / `detect`

A good thing about the methods in Ruby is that you can pretty much figure out what they do just by their name.

**Think About It**
What do you think `find` or `detect` does? What will it return?  

`find` will return the **first** item from the collection that evaluates as _truthy_.

But before we go into how that works, let's implement it with `each`.

```ruby
def find_me_first_even
  numbers = [1, 2, 3, 4, 5]

  numbers.each do |num|
    return num if num.even?
  end

end
```

We walk through the array, and upon the first number it comes across that makes the block return true, it just returns the item and we are done.

This looks like fairly simple code, but we can make it cleaner with `.find`.

```ruby
def find_me_first_even
  numbers = [1,2,3,4,5]

  numbers.find do |num|
    num.even?
  end

end
```

Oh just look at that, so nice. Remember, it will return the **first** item for which the block returns a truthy value.

#### Independent Practice  
Find the first sister over four letters in length.

```ruby
def find_sisters
  sisters = ["Rose", "Kathleen", "Eunice", "Patricia", "Jean"]

  sisters.find do |sister|
    # YOUR CODE HERE
  end
end
```
**FlashCard**

Its time to create your next flashcard!  Using the same format that we used for \#map, create a flashcard for \#find - including syntax, return value, and use-cases.

**Turn & Talk**  
Share you flashcard with your neighbor.  Talk them through it and be specific. What is similar/different? Are there any changes/additions you want to make to your own flashcard?  

### `find_all` / `select`

We've figured out how to get _one_ matching thing out of an array, but what if we want ALL of the matching things?

Let's start by thinking about how we would do this using our old friend, `.each`.

```ruby
def all_the_odds
  numbers = [1,2,3,4,5]

  result = []

  numbers.each do |num|
    result << num if num.odd?
  end

  result

end
```

How does this look?

Not bad, but we're stuck with that `result` container that we don't like. Pay attention to this - it's a pattern we want to keep an eye out for in the future. **If we are catching things with a collector like this, there's probably a better enumerable that we can use.** So let's use `.select`.

```ruby
def all_the_odds
  numbers = [1,2,3,4,5]

  numbers.select do |num|
    num.odd?
  end

end
```

**FlashCard**

Its time to create your next flashcard!  Using the same format that we used for \#find, create a flashcard for \#find_all - including syntax, return value, and use-cases.

**Turn & Talk**  
Share you flashcard with your neighbor.  Talk them through it and be specific. What is similar/different? Are there any changes/additions you want to make to your own flashcard?

### Additional Enumerables

Now that we have walked through 3 of the most common Enumerables as a class, its time for you and your partner to do some independent research!  Working with your partner, research the following Enumerables and make flashcards for each based on what you find.  The [Enumerable Ruby docs](https://ruby-doc.org/core-2.4.1/Enumerable.html) will be a great place to start!

* \#max
* \#min
* \#max_by
* \#min_by
* \#sort_by
* \#all?
* \#any?
* \#none?
* \#one?


## Final CFU
* What do map, find, and select do? What do they return?
* What do max, max_by, their opposites, and sort_by return?
* What makes an enumerable preferable to each?
* What does the `?` on the end of a method indicate?  


### Additional Practice

[Enums-Exercises](https://github.com/turingschool/enums-exercises).
