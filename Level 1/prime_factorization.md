# usage 

- get the prime factors of a number
  
# main idea

- every composite number(not-prime) hav atleast 1 prime below sqrt(n) so we check until sqrt(n)
- if the remaining is not 1 then the number is prime

# time complexity
  ### Sqrt(n)

# code

```cpp
vector<int> prime_factorization(int num) {
    vector<int> factors;
    if (num < 2) return factors;
    while (!(num % 2)) {
        factors.push_back(2);
        num /= 2;
    }
    for (ll i = 3; i * i <= num; i += 2) {
        while (!(num % i)) {
            factors.push_back(i);
            num /= i;
        }
    }
    if (num > 1) factors.push_back(num);
    return factors;
}
```
