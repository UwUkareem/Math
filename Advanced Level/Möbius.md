# The Möbius function (μ(n)):
The Möbius function is defined as:
- μ(n) = 1 if n = 1.
- μ(n) = 0 if n is divisible by any perfect square greater than 1 (square free).
- μ(n) = (-1)^k if n is the product of k distinct prime numbers.

https://en.wikipedia.org/wiki/M%C3%B6bius_function

```cpp
const int MAXN = 100000;
vector<int> mu(MAXN + 1, 1);
vector<int> prime(MAXN + 1, 1);

void compute_mobius() {
    mu[1] = 1;
    for (int i = 2; i <= MAXN; ++i) {
        if (prime[i]) {
            for (int j = i; j <= MAXN; j += i) {
                prime[j] = 0;
                mu[j] *= -1;
            }
            for (int j = i * i; j <= MAXN; j += i * i) {
                mu[j] = 0;
            }
        }
    }
}
```

# Möbius inversion

https://en.wikipedia.org/wiki/M%C3%B6bius_inversion_formula -> Proofs of generalizations
https://codeforces.com/blog/entry/53925

- d∣n∑ μ(d)=ε(n)
 the formula tells us that when you sum the Möbius function over all divisors of n, it "collapses" to 1 only if n = 1 and 0 for all other integers.

start explain 

[gcd(i,j) = 2] -> [gcd(i,j)/2 = 1] 












