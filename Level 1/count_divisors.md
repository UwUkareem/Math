# usage 

- count the number of divisors

# main idea

- we just iterate until sqrt(n)

# time complexity
  ### Sqrt(n)

# code

```cpp
int count_divisors(int num) {
    int i, counter = 0;
    for (i = 1; i * i < num; i++) {
        if (!(num % i)) counter += 2;
    }
    if ((i * i) == num) counter++;
    return counter;
}
```


# by prime fact
- number of divisors = pow1+1 * pow2+1 * ..

  ex : 12 = 2^2 * 3^1 -> no div = 2+1 * 1+1 = 6
