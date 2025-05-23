### Introduction

Use what you have learnt about recursion so far to tackle two classic problems that can leverage recursion: Fibonacci and Merge Sort.

#### Fibonacci

The [Fibonacci Sequence](http://en.wikipedia.org/wiki/Fibonacci_number), is a numerical sequence where each number is the sum of the two numbers before it. Eg. 0, 1, 1, 2, 3, 5, 8, 13 are the first eight digits in the sequence.

You should already be thinking that perhaps this can be solved iteratively rather than recursively, and you would be correct. Nevertheless generating the sequence recursively is an excellent way to better understand recursion.

You can watch this [video from Khan Academy on recursive Fibonacci](https://www.youtube.com/watch?v=zg-ddPbzcKM) to understand it further.

#### Merge sort

A significant part of computer science is dedicated to sorting data. An algorithm which uses the 'divide and conquer' approach of recursion is able to reduce a sorting problem to smaller and smaller sub-problems.

Merge sort is one such sorting algorithm, and can be much faster than other algorithms such as bubble sort on the right data sets. Essentially merge sort recurses through an array of unsorted data until it reaches its smallest sub-set, a single item. Of course an array with a single item is considered sorted. Merge sort then merges the single items back together in sorted order. Pretty clever!

To understand what the merge sort algorithm is doing check out these resources:

1. Watch this introductory video on [merge sort from Harvard's CS50x course](https://youtu.be/Ns7tGNbtvV4).
1. Watch another explanation of [how merge sort works](https://www.youtube.com/live/iCx3zwK8Ms8?si=t7z6bEv_ZXIJDoHU&t=6550) (watch only until 2:04:05), this time from a part of a Harvard CS50x lecture.
1. [The concept of merging](https://youtu.be/6pV2IF0fgKY) and [Merge Sort -- How it Works part](https://youtu.be/mB5HXBb_HY8) on YouTube give you a more formal look at this problem if you're still unclear.
1. (Optional) Play with this [Merge Sort Visualizer](https://www.hackerearth.com/practice/algorithms/sorting/merge-sort/visualize/) to get a better feel for exactly what is happening during a Merge Sort.

<div class="lesson-note lesson-note--tip" markdown="1">

#### Running your project code

You will need a way to run the scripts you create for this project. Because there is no GUI component to this project it should be run in the command line rather than the browser.

JavaScript files can be run directly from the command line using the node command installed with nodejs. You can learn about the common ways to do this by reading the [documentation for the Node CLI](https://github.com/nodejs/nodejs.dev/blob/aa4239e87a5adc992fdb709c20aebb5f6da77f86/content/learn/command-line/node-run-cli.en.md).

</div>

### Assignment

<div class="lesson-content__panel" markdown="1">

First up create a file and tackle the fibonacci sequence:

1. Using iteration, write a function `fibs` which takes a number and returns an array containing that many numbers from the Fibonacci sequence. Using an example input of `8`, this function should return the array `[0, 1, 1, 2, 3, 5, 8, 13]`.
1. Now write another function `fibsRec` which solves the same problem recursively.
1. Test both versions of your functions by passing in various lengths as arguments.

Hopefully you were able to solve the problem with recursion! If you need some help understanding what's going on with this function, the "Test it out" section below will help. If you're still a bit confused, there are some additional resources linked at the end of this page.

Once you have a firm grasp on solving Fibonacci with recursion, create a new file and work on a merge sort:

1. Build a function `mergeSort` that takes in an array and returns a sorted array, using a recursive merge sort methodology. An input of `[3, 2, 1, 13, 8, 5, 0, 1]` should return `[0, 1, 1, 2, 3, 5, 8, 13]`, and an input of `[105, 79, 100, 110]` should return `[79, 100, 105, 110]`.

Tips:

- Think about what the base case is and what behavior is happening again and again and can actually be delegated to someone else (e.g. that same function!).
- It may be helpful to check out the background videos again if you don't quite understand what should be going on.

#### Test it out

To showcase the recursive effect implemented in your Fibonacci function, do the following:

1. Add the following to the start of the function:

   ```javascript
   console.log("This was printed recursively");
   ```

1. Call the function with `8` as the argument.
1. If the function is implemented correctly, you should see that sentence printed around 8 times (keep in mind that, depending on the way you implemented the function, you may see 7 instead of 8. This isn't a bug! It simply depends on how many times the function is *actually* repeated).

</div>

### Additional resources

This section contains helpful links to related content. It isn't required, so consider it supplemental.

- An extensive written JavaScript solution for [recursive Fibonacci](https://www.scaler.com/topics/fibonacci-series-in-javascript/)
- Another look at [merge sort](http://www.sorting-algorithms.com/merge-sort)
- Visualize and understand the [memory allocation for recursive functions](https://www.educative.io/courses/recursion-for-coding-interviews-in-javascript/NEZ7kKgMJKK).
- For more attempts at recursion try the first 5 problems in [Project Euler](https://projecteuler.net/problems)
