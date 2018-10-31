##Sorting

First we tried to implement counting sort, because it runs in linear time and there are a limited number of lrmus lengths.
However, it couldn't handle tiebreakers like alphabetical order because those don't fit counting sort.

Next we tried radix sort, by considering the tiebreakers as digits and
using Arrays.Sort for each, but it ended up being slower than using Arrays.sort
with the original comparator.

Next we implemented quicksort (with a switch to insertion sort for the last 10) which
runs slightly faster, and sorts the items correctly. 

We also modified the compareTo function, and we hoped it would be faster by using subtracting instead of a comparison, but it made no difference.

##Finding the LRMUS
We changed updateAt so that the string toMatch is always at least as long as the current lrmus, which saved
about 100ms. Here's the change:
```
for(int end=start + length; end<n;end++){
//this used to be:
for(int end=start; end<n;end++){
```
This also required us to change the starting value for `length` to 0 instead of `Integer.MIN_VALUE`
After making that change we removed the redundant comparisons in the function.

We tried to change the for loop in the findBest() function so that when you get near the end you don't call
updateAt() if it can't produce an lrmus longer than the current best, but the operation in the for loop actually made it
slower. Here's what it looked like:

```
public void findBest(){
  for(int i =0; i< referenceStr.length()-length;i++){
      updateAt(i);
  }
}
```

All of the code was done together at the lab. We used pair programming where we switched from time to time.

GroupZ was our attempt at radix sort. Our submission is Group2.


