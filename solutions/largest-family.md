```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int n, answer = 0;
    cin >> n;
    vector<string> arr(n);
    for (int i = 0; i < n; i++)
        cin >> arr[i];
    unordered_map<string, int> anagrams;
    for (int i = 0; i < n; i++) {
        sort(arr[i].begin(), arr[i].end());
        anagrams[arr[i]]++;
        answer = max(answer, anagrams[arr[i]]);
    }
    cout << answer;
    return 0;
}
```
