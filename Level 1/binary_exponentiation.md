# usage 

- fatest way to calc power of a number

# main idea

- if the power is even we turn it into : n^pow = n^(2*(pow/2)) = (n^2)^(pow/2)
- if the power is odd we multiply in current base and new_pow = pow-1

# ex
2^13 = 2 * 2^12 = 2 * ( (2^2)^(12/2) ) =
2 * (4^6) = 2 *  (16^3) = 2 * 16 * (16^2) =  2 * 16 * (256^1) = 2 * 16 * 256


# time complexity
  ### log(n)

# code

```cpp
int binaryexponentian (int a, int b) {
    int res = 1;
    while (b > 0) {
        if (b & 1)
            res = res * a;
        a = a * a;
        b /= 2;
    }
    return res;
}
```

# code with mod

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
```

```cpp
int quick_pow(int a,int b,int p){
    int c=1;
    for(;b;b>>=1){
        if(b&1){c=c*a;if(c>=p)c=c%p+p;}
        a=a*a;if(a>=p)a=a%p+p;
    }
    return c;
}
```
