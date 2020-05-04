You will be given a range `L` and `R` (both inclusive). Find the summation of all prime numbers in this range.

**Input Format**

 - First line contains a single integer `Q`
 - Next `Q` lines contain two integers `L` and `R` respectively.

**Constraints**

 - `Q` <= `100`
 - `1` <= `L`, `R` <= `1000000`
 - `L < R`

**Output Format**

A single integer denotes the sum of prime numbers on every line.

**Sample Input**
```
2
1 9
4 13
```

**Sample Output**
```
17
36
```

**Explanation**

```
2 + 3 + 5 + 7 = 17
5 + 7 + 11 + 13 = 36
```

---

# Solution

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
