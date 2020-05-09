```cpp
#include <bits/stdc++.h>
using namespace std;
unsigned long long int fibonacci(int n) {
    vector<unsigned long long int> arr(n+2,0);
    if(n==0 || n==1)
        return 1; 
    arr[0]=1;
    arr[1]=1;
    for(int i=2;i<=n;i++)
        arr[i]=arr[i-1] + arr[i-2];
    return arr[n];
}
int main() {
        int n;
        cin >> n;
        cout << fibonacci(n)<<"\n";
    return 0;
}
```
