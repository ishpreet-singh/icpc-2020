# Modular Exponentiation

Raising `a` to the power of `n` is expressed naively as multiplication by `a` done `n−1` times: `a^n=a⋅a⋅…⋅a`. However, this approach is not practical for large a or n.

![large a](https://github.com/ishpreet-singh/icpc-2020/blob/master/Others/common/images/week-1/large-a.png)

The idea of binary exponentiation is, that we split the work using the binary representation of the exponent.

Let's write n in base 2, for example:

![example](https://github.com/ishpreet-singh/icpc-2020/blob/master/Others/common/images/week-1/ex1-part1.png)

Since the number n has exactly ⌊log2n⌋+1 digits in base 2, we only need to perform **`O(logn)`** multiplications, if we know the powers a,a^2,a^4,a^8,…,a^⌊logn⌋.

So we only need to know a fast way to compute those. Luckily this is very easy, since an element in the sequence is just the square of the previous element.

![example](https://github.com/ishpreet-singh/icpc-2020/blob/master/Others/common/images/week-1/ex1-part2.png)

So to get the final answer for 3^13, we only need to multiply three of them (skipping 32 because the corresponding bit in n is not set): 3^13=6561⋅81⋅3=1594323

The final complexity of this algorithm is **`O(logn)`**: we have to compute logn powers of a, and then have to do at most logn multiplications to get the final answer from them.

The following recursive approach expresses the same idea:

![Recursive Binary](https://github.com/ishpreet-singh/icpc-2020/blob/master/Others/common/images/week-1/recusive-binary.png)

Recursive approach
```
long long binpow(long long a, long long b) {
    if (b == 0)
        return 1;
    long long res = binpow(a, b / 2);
    if (b % 2)
        return res * res * a;
    else
        return res * res;
}
```


Iterative Approach:
```
long long binpow(long long a, long long b) {
    long long res = 1;
    while (b > 0) {
        if (b & 1)
            res = res * a;
        a = a * a;
        b >>= 1;
    }
    return res;
}
```


Compute **`(x^n)%m`**. This is a very common operation. For instance it is used in computing the modular multiplicative inverse.

Solution: Since we know that the module operator doesn't interfere with multiplications 

`(a⋅b≡(amodm)⋅(bmodm)(modm))`, 

we can directly use the same code, and just replace every multiplication with a modular multiplication:

```
long long binpow(long long a, long long b, long long m) {
    a %= m;
    long long res = 1;
    while (b > 0) {
        if (b & 1)
            res = res * a % m;
        a = a * a % m;
        b >>= 1;
    }
    return res;
}
```