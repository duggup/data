Ravi has a dream to be a King. One of the rule in his kingdom will be that for a couple to name their kids they have to choose only from certain number of alphabets. So, if a couple choose a,b and c alphabets their children's names can be abc,acb,cab,etc. These sets of alphabets are unique for every couple. You being a minister in Ravi's ministry has the task to find out the size of largest family in kingdom.

Input Format

First line contains N i.e. Number of children in kingdom.

Second line contains N space separated strings denoting name of child.

(Only lower case letters are used to form names)

Constraints

1<= N <= 10000000

length of name <= 100

Output Format

Single integer denoting size of largest family.

Sample Input 0

5
abc
cab
pqr
xyz
rst

Sample Output 0

2

Explanation 0

abc and cab belongs to same family.

---

# Solution

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
