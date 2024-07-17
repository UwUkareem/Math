# multiples loop

```cpp
const int N = 1000005;
vector<int> dv[N];
void get_divisors() {
    for(int i=1;i<N;++i)
    {
        for(int j=i;j<N;j+=i)
        {
            dv[j].push_back(i);
        }
    }
}
```
