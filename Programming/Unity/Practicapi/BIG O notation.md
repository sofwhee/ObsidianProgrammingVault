To measure code performance, use Big o notation.

Measured by algorithm's worst-case scenario.

## Example

To check if all numbers in an array are above a certain number..
Worst case scenario, we have to enter the loop for every number.

Or, better put...

We might have to enter the loop up to `n` times.
`n` = number of elements in the array
`0(N)`

If the array is 2 dimensional...
We might have to enter the loop for every number
And then again for every number inside that number's array
It has exponentialized once now, so...
`0(N^2)`

The `^2` captures how many times it has exponentialized, minus one.