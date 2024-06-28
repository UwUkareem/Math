# main idea
- like sieve but instead of 1 : N
- it work from L : L+1e7
- we calc sieve primes until sqrt(R) sor max R = 1e14

#code o(n)

```cpp
// call segmentedSieve in main and give it L & R
void simple_sieve(vector<int>& prime, int high){
    bool ck[high + 1];
    memset(ck, true, sizeof(ck));
    ck[1] = false;
    ck[0] = false;
    for (int i = 2; (i * i) <= high; i++) {
        if (ck[i]) {
            for (int j = i * i; j * j <= high; j = j + i) {
                ck[j] = false;
            }
        }
    }
    for (int i = 2; i * i <= high; i++) {
        if (ck[i]) {
            prime.push_back(i);
        }
    }
}

vector<int> segmentedSieve(int low, int high){
    if (low<2 and high>=2){
        low = 2;
    }
    bool prime[high - low + 1];
    memset(prime, true, sizeof(prime));
    vector<int> chprime;
    simple_sieve(chprime, high);
    for (int i : chprime) {
        int lower = (low / i);
        if (lower <= 1) {
            lower = i + i;
        }
        else if (low % i) {
            lower = (lower * i) + i;
        }
        else {
            lower = (lower * i);
        }
        for (int j = lower; j <= high; j = j + i) {
            prime[j - low] = false;
        }
    }
    vector<int> p;
    for (int i = low; i <= high; i++) {
        if (prime[i - low]) {
            p.push_back(i);
        }
    }
    return p;
}
```
