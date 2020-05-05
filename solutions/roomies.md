```cpp
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
