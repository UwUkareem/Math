# usage of ETF

- from 1 : N it counts the numbers which are co-prime with N -> gcd(number,N) = 1
- ex: phi(5) = 4 -> gcd(5, 1 2 3 4 ) = 1

# ETF AND prime numbers

### phi(P) = P - 1
- ex: phi(7) = 6

# ETF AND prime power x

- phi(P^x) = P^x - numbers from 1 : P^x which are not co-primes
- numbers from 1 : p^x which are not co-primes = multiples of P
- so: phi(P^x) = P^x - Number of multiple of P
- Number of multiple of P = P^x / P
- ex: Number of multiple of 3 until 100 = 100 / 3 = 33
- so the final formula is : phi(P^x) = P^x - (P^x / P) =  P^(x-1) * (P - 1)
  
### phi(P^x) = P^(x-1) * (P - 1)

# ETF AND any number 

## multiplicative Rule

- f(N*M) = f(N) * f(M) iff gcd(N, M) = 1, IF THIS IS TRUE we call f multiplicative
- we use this in : f(N) = f(p1^x1) * f(p2^x2) * ... (prime factors are co-primes)
- ex: number of divisors using prime fact -> 24 = 2^3 * 3^1 -> no div = (3+1) * (1+1) = 8

## etf for any number Sqrt(n)

- we get the prime factors of the number
- phi(P^x) = P^(x-1) * (P - 1)
- then multiplicative rule we multiply all phi we got
- phi(N) = [ P1^(x1-1) * (P1 - 1) ] * [ P2^(x1-1) * (P2 - 1) ] * ....
- we can simplify it into
### phi(N) = N * ( (p1-1) / p1 ) *  ( (p2-1) / p2 ) * ...

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
## etf for queries number Nlog(log(N)) using sieve 1:1e6
- initalize an array with values = indexes ie {1,2,3,4,,}
- we iterate startin from 2 if the value still == the indx -> this is a prime number
- now we will do an operation on this nmuber and all its multiples
- the operation is : we divide by the prime then multiply * (prime -1)
- ex 3 : we 3/3 * 2 , 6/3 * 2 and so on

```cpp
const int N = 1000005;
vector<int> phi(N + 1);
void phi_1_to_n() {
    for (int i = 1; i < N; i++)
        phi[i] = i;
    for (int i = 2; i < N; i++) {
        if (phi[i] == i) { // this is prime
            for (int j = i; j < N; j += i)
                phi[j] -= phi[j] / i;
        }
    }
}
```

### notes 
- if p is prime  phi(p^k) = p^k - p^(k-1)
- phi(a*b*c) = phi(a) * phi(b) * phi(c)
- phi(n^k) = n^(k-1) * phi(n)
- n = sum of phi(disiors of n)
- phi(N!)
```cpp
// phi(N!) = (N is prime ? N-1 : N ) * phi((N-1)!)
ll phi_factn(int n)
{
    ll ret = 1;
    for (int i = 2; i <= n; ++i)
        ret = ret * (isprime(i) ? i-1 : i);
    return ret;
}
```




