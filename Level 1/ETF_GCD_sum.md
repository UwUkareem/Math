# ( i = 1 : N )Σ GCD(i,N), u hav q queries
## observations
- gcd(i,N) = a divisor of N -> sqrt(n)
- instead of looping from 1 to N we will loop till i*i -> sqrt
- in other words we wiil loop on the divisors
- now we check how many numbers the gcd of it and N = this divsor
- ie: gcd(numbers,N) = d
- we will use etf to obtain these "numbers"
- how many numbers from 1:N that have gcd = d with N ?
- gcd(i, N) = d -> gcd(i/d , N/d) = 1 //we remove the biggest common thing already
- note 1 <= i/d <= N/d
- so we calc phi(N/d) and that's the no. numbers whats have gcd = d with N from 1:N
- we use sieve_phi to generate all the phi fro queires

## Nlog(N) + q*sqrt(N)
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
int count_etf(int d, int n){
    return phi[n/d];
}
int gcd_sum(int n){
    int res = 0;
    for (int i = 1; i*i <= n; ++i) {
        if(n%i != 0){
            int d1 = i, d2 = n/i;
            res+= d1 * count_etf(d1, n);
            if(d1!=d2)
                res+= d2 * count_etf(d2, n);
        }
    }
    return res;
}
```
