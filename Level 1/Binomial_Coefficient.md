# infos

- given q queries N, K & given prime P
- find C(N, K) % P
- if P > N normal method
- if P < N locus theorm

# normal method

## main idea

- C(N, K) %P = N! %P / ( K! %P * (N-K)! %P )

### generate all factorials for queries
```cpp
const int N = 1e6, mod = 1e9 + 7;
int factorial[N];

void generate_fact() {
    factorial[0] = 1;
    for (int i = 1; i < N; ++i) {
        factorial[i] = i * factorial[i - 1] % mod;
    }
}
```
### calculating C
```cpp
int modular_binaryexponentian (int a, int b, int c) {
    int res = 1;
    while (b > 0) {
        if (b & 1)
            res = (res * a)%c;
        a = ((a%c) * (a%c))%c;
        b /= 2;
    }
    return res;
}
ll inverse(ll b) { return modular_binaryexponentian(b, mod - 2, mod); }
ll C(int n, int k) {
    if(k>n)
        return 0;
    return factorial[n] * inverse(factorial[n - k]) % mod * inverse(factorial[k]) % mod;
}
```

### calculating P
```cpp
ll P(int n, int k) {
    return factorial[n] * inverse(factorial[n - k]) % mod;
}
```
