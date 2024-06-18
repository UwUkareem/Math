# usage 

- count the number of divisors

# main idea

- we just using iterate until sqrt(n)

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
