Sita and Gita are roomies. One of them always forgets to carry the room's key and use it to call the other for help. So, their friend Seema had a superb plan. A lock with a pin. Sita and Gita go to buy a new lock, but not a normal lock.

The lock has `4` circular wheels. Each wheel has `10` slots: `0-9`. The wheel can rotate freely and wrap around(`9 -> 0` and `9 <- 0`). Each move consists of turning one wheel one slot. Initially, lock starts at `0000`, a string representing the state of `4` wheels. The lock has few dead ends, which means if lock displays any of these codes, the wheels of the lock will stop turning and you will be unable to open it.

Given a target representing the value of the wheel that will unlock the lock, calculate the minimum total number of turns required to open the lock, or -1 if it's impossible.

**Input Format**

 - the first line consists of single integer denoting the number of dead-ends `n`
 - next `n` lines have a string with length `4` denoting a dead-end state
 - the last line has a string with length `4` denoting pin to open the lock.

**Constraints**

Number of deadends <= `10`

**Output Format**

A single integer denoting the number of movements.

**Sample Input**

```
5
0201
0101
0102
1212
2002
0202
```

**Sample Output**

```
6
```

**Explanation**

```
0000 -> 1000 -> 1100 -> 1200 -> 1201 -> 1202 -> 0202
```

---

# Solution

```
#include<bits/stdc++.h>
using namespace std;
int BFS(vector<string>& deadends, string target) {
        vector<int> visited(10001);
        string s="0000";
        queue<string> qu;
        qu.push(s);
        visited[0]=1;
        int step=0;
        for(auto& x:deadends)
        {
            if(x=="0000")
                return -1;  // cannot reach target if target itself is a deadend
            int a=stoi(x);
            visited[a]=1;  // marking visited for all deadends
        }
        while(!qu.empty())  // BFS loop
        {
            int len=qu.size();
            while(len>0)
            {
                len--;
                string current=qu.front();
                qu.pop();
                if(current==target)
                    return step;
                for(int i=0;i<4;i++)        // generating all possible permutations from current state
                {
                    char curC=current[i];
                    char nextC=curC=='9' ? '0':curC+1;
                    char lastC=curC=='0' ? '9':curC-1;
                    current[i]=nextC;
                    int temp=stoi(current);
                    if(!visited[temp])
                    {
                        qu.push(current);
                        visited[temp]=1;
                    }
                    current[i]=lastC;
                    temp=stoi(current);
                    if(!visited[temp])
                    {
                        qu.push(current);
                        visited[temp]=1;
                    }
                    current[i]=curC;
                }
            }
            step++;
        }
        return -1;
    }
int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */  
    vector<string> deadends;
    string target;
    int n;
    cin>>n;
    while(n--)
    {
        string s;
        cin>>s;
        deadends.push_back(s);
    }
    cin>>target;
    cout<<BFS(deadends,target);
    return 0;
}
```
