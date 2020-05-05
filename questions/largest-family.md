Ravi has a dream to be a King. One of the rules in his kingdom will be that for a couple to name their kids they have to choose only from a certain number of alphabets. So, if a couple chooses `a`, `b`, and `c` alphabets their children's names can be `abc`, `acb`, `cab`, etc. These sets of alphabets are unique for every couple. You being a minister in Ravi's ministry has the task to find out the size of the largest family in the kingdom.

**Input Format**
 - First line contains `N` i.e. Number of children in kingdom.
 - Second line contains `N` space separated strings denoting name of child.

> Only lower case letters are used to form names

**Constraints**

 - `1` <= `N` <= `10000000`
 - length of name <= `100`

**Output Format**

Single integer denoting size of largest family.

**Sample Input**
```
5
abc
cab
pqr
xyz
rst
```

**Sample Output**

```
2
```

**Explanation**

`abc` and `cab` belongs to the same family.
