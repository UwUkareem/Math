# main idea

- Gcd(a,b) = a  if b = 0
- Gcd(a,b) = Gcd(b,a%b)  if b != 0
- ex : gcd(140,12) = gcd(12,8) = gcd(8,4) = gcd(4,0) = 4

# notes

- gcd(a,b) = gcd(b,a)
- gcd(a,b) = gcd(a-b,b) = gcd(a,b-a)

# calculation 
we replace the bigger number with the mod of it with the other one 
- if a > b , gcd(a,b) = gcd(a%b,b) and so on until 0 appear

# for big numbers
- gcd(bignum1,num2)-> get divsors of num2
- try every div of num2 with bignum1
- we pick the biggest div and this is the gcd
- if there's a power u can use modulo operation
# time
## log(n)
# code
## recursive 
```cpp
int gcd (int a, int b) {
    if (b == 0)
        return a;
    else
        return gcd (b, a % b);
}

```
## iterative 
```cpp
int binary_gcd(int a, int b) {
    if (!a || !b)
        return a | b;
    unsigned shift = __builtin_ctz(a | b);
    a >>= __builtin_ctz(a);
    do {
        b >>= __builtin_ctz(b);
        if (a > b)
            swap(a, b);
        b -= a;
    } while (b);
    return a << shift;
}
```
## LCM
```cpp
int lcm (int a, int b) {
    return a / gcd(a, b) * b;
}
```

## number of steps gcd
```cpp
int gcd_steps(int a, int b) {
    if (!a)
        return 0;
    if (!b)
        return 1;
    if (a >= b){
        int aa = a % b;
        int bb = a / b;
        if (bb % 2 == 1) {
            return gcd_steps(b, aa) + bb + bb/2;
        } else {
            return gcd_steps(aa, b) + bb + bb/2;
        }
    }
    return 1 + gcd_steps(b, abs(a - b));
}
```
## number of pairs with gcd d & satisfying a+b = k is phi[k/d]
