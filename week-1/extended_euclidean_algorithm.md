# Extended Eucledean Algorithm

While the Euclidean algorithm calculates only the greatest common divisor (GCD) of two integers a and b, the extended version also finds a way to represent GCD in terms of a and b, i.e. coefficients x and y for which:

`a⋅x+b⋅y=gcd(a,b)`

## Algorithm:


![Extended Euclidean](https://github.com/ishpreet-singh/icpc-2020/blob/master/images/week-1/extended-euclidean.png)


## Implementation

```
int gcd(int a, int b, int & x, int & y) {
    if (a == 0) {
        x = 0;
        y = 1;
        return b;
    }
    int x1, y1;
    int d = gcd(b % a, a, x1, y1);
    x = y1 - (b / a) * x1;
    y = x1;
    return d;
}
```

The recursive function above returns the GCD and the values of coefficients to x and y (which are passed by reference to the function).

Base case for the recursion is a=0, when the GCD equals b, so the coefficients x and y are 0 and 1, respectively. In all other cases the above formulas are used to re-calculate the coefficients on each iteration.

This implementation of extended Euclidean algorithm produces correct results for negative integers as well.

## Practice Problems

