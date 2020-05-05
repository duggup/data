```cpp
#include <bits/stdc++.h>
using namespace std;
int LIM = 1000001
vector<long> primes(LIM, -1);
void sieve() {
    primes[0] = primes[1] = 0;
    for(long i = 2; i < LIM; i++) {
        if(primes[i] == 0)
            continue;
        primes[i] = i;
        long j = 2;
        while(i*j < LIM) {
            primes[i*j] = 0;
            j++;
        }
    }
    for(long i = 1; i < LIM; i++) {
       primes[i] += primes[i-1];
    }
}
int main() {
    sieve();
    long tests;
    cin >> tests;
    while(tests--) {
        long left, right;
        cin >> left >> right;
        if(left != 0) {
            cout << primes[right]-primes[left-1] << endl;
        } else {
            cout << primes[right] << endl;
        }
    }
    return 0;
}
```
