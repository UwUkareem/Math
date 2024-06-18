# usage 

- get the divisors of a number

# main idea

- we just iterate until sqrt(n)

# time complexity
  ### Sqrt(n)

# code

```cpp
vector<int> get_divisors(int num) {
    vector<int> divisors;
    ll i;
    for (i = 1; i * i < num; i++) {
        if (!(num % i)) {
            divisors.push_back(i);
            divisors.push_back(num / i);
        }
    }
    if((i * i) == num) divisors.push_back(i);
    return divisors;
}
```
