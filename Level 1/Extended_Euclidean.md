# found solutions for: ax + by = gcd(a,b) 
- bezout lemma : given a & b -> there is a sol for : ax + by = d

# first how normal eucildian work
- ex : 81 & 57
- 81 = 1 * 57 + 24 (rem)
- 57 = 2 * 24 + 9
- 24 = 2 * 9 + 6
- 9 = 1 * 6 + 3
- 6 = 2 * 3 + 0
- gcd(81,57) = 3

# Extended Euclidean is the reverse of this process
- we start from : 9 = 1 * 6 + 3
- 9 - 1 * 6 = 3 -> ax + by = gcd
- 9 - 1 * ( 24 - (2 * 9)) = 3 -> from previous eq
- last eq -> gcd = gcd * x + 0 * y
- so the base case can be x = 1 & y = 0 (any val)
- if we cal this we can calc the eq above it ans so on

# code recursive

```cpp
// send x , y the sol of eq stored on them
int gcd(int a, int b, int& x, int& y) {
    if (b == 0) {
        x = 1;
        y = 0;
        return a;
    }
    int x1, y1;
    int d = gcd(b, a % b, x1, y1);
    x = y1;
    y = x1 - y1 * (a / b);
    return d;
}
```

# code iterative

```cpp
int gcd(int a, int b, int& x, int& y) {
    x = 1, y = 0;
    int x1 = 0, y1 = 1, a1 = a, b1 = b;
    while (b1) {
        int q = a1 / b1;
        tie(x, x1) = make_tuple(x1, x - q * x1);
        tie(y, y1) = make_tuple(y1, y - q * y1);
        tie(a1, b1) = make_tuple(b1, a1 - q * b1);
    }
    return a1;
}
```
