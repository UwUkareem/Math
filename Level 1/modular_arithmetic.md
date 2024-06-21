# summation & subtraction & multiplication 
### congruent
- a%N == b%N -> a and b are congruent -> so we can replace a and b with each other in any modular operation
- we can write it like that ( a ≡ b (mod N) )
- a = kN + b 

### modulo operation
- (a+b)%N = ( (a%N) + (b%N) )%N
- (a*b)%N = ( (a%N) * (b%N) )%N

### exponentiation
- a^k %N = ( (a%N) ^ k )%N


# division 
- multiplicative inverse of 5 is 1/5
- so (a/b) % c = (a%c  * (1/b)%c) %c
- we have to find 'modulo' multiplicative inverse of b
- lets call modulo multiplicative inverse N
- N*b %c = 1 -> we find N
- (a/b) % c = (a%c  * N%c) %c

### notes
- not all numbers have modulo multiplicative inverse
- the gcd(b,c) = 1 -> b: denominator  , c: the mod <<<<< co-primes >>>>>

## calculation

- ## extended euclidian algorithm (mod is prime & not-prime)
```cpp
ll gcdExtended(int a, int b, int* x, int* y)
{
    if (a == 0) {
        *x = 0, *y = 1;
        return b;
    }
    int x1, y1;
    int gcd = gcdExtended(b % a, a, &x1, &y1);
    *x = y1 - (b / a) * x1;
    *y = x1;
    return gcd;
}
int modInverse(int A, int M)
{
    int x, y;
    int g = gcdExtended(A, M, &x, &y);
    int res = (x % M + M) % M;
    return res;
}
```

- ## fermat's little theorem (mod is prime)
- if we have number a and 'prime' mod m
- modulo inverse for a is a^(m-2)
- we use binary_expo code log(m-2)
- m must be primeeee to use fermat if not we use euler
- a&m must be co-primes so there is modulo inverse

- ## Euler's Totient function (mod is prime or not-prime)
- if we have number a and 'not prime' mod m
- we find phi(m)
- modulo inverse for a is a^(phi(m) - 1)

- ### finding phi O(sqrt(m))
```cpp
int phi(int n) {
    int result = n;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            while (n % i == 0)
                n /= i;
            result -= result / i;
        }
    }
    if (n > 1)
        result -= result / n;
    return result;
}
```

- ### finding phi from 1 to n  O(nloglog(n))
```cpp
void phi_1_to_n(int n) {
    vector<int> phi(n + 1);
    for (int i = 0; i <= n; i++)
        phi[i] = i;

    for (int i = 2; i <= n; i++) {
        if (phi[i] == i) {
            for (int j = i; j <= n; j += i)
                phi[j] -= phi[j] / i;
        }
    }
}
```






