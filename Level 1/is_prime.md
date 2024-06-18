# main idea

- we can get all divisors of a number by iterating sqrt(n),
   if we found a number divisible by n we can get the other divisor (n/number)
- even numbers "except 2" aren't prime so all the even divisors aren't prime

# implementation

- check if number is even "except 2"
- iterate through the odd divisors until sqrt(n)

# time complexity
  ### Sqrt(n)

# code

```cpp
bool is_prime(int num) {    
    if (num == 2) return true;
    if (num < 2 || !(num % 2)) return false;
    for (int i = 3; i * i <= num; i += 2) {
        if (!(num % i)) return false;
    }
    return true;
}
```
