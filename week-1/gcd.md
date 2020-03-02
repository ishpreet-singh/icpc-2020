# GCD

Given two non-negative integers a and b, we have to find their GCD (greatest common divisor), i.e. the largest number which is a divisor of both a and b. 

The algorithm is extremely simple:

![GCD](https://github.com/ishpreet-singh/icpc-2020/blob/master/images/week-1/gcd.png)

### Implementation:

```
int gcd (int a, int b) {
    if (b == 0)
        return a;
    else
        return gcd (b, a % b);
}
```

Time complexity if: **`O(logmin(a,b))`**


## LCM

Calculating the least common multiple (commonly denoted LCM) can be reduced to calculating the GCD with the following simple formula:

![GCD](https://github.com/ishpreet-singh/icpc-2020/blob/master/images/week-1/lcm.png)

### Implementation

```
int lcm (int a, int b) {
    return a / gcd(a, b) * b;
}
```

## Practice Problems

* [GCD and LCM](https://www.codechef.com/problems/FLOW016)
