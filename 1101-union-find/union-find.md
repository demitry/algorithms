<!-- TOC -->

- [Union-Find](#union-find)
    - [Dinamic connectivity](#dinamic-connectivity)
        - [Ex: applications:](#ex-applications)
    - [quick find](#quick-find)
    - [quick union](#quick-union)
    - [improvements](#improvements)
    - [applications](#applications)

<!-- /TOC -->

## Union-Find

### Dinamic connectivity
Given a set of N objects
- Union Command: connect two objs
- Find/connected query - is there a path connecting the two objects?

#### Ex: applications:
- Pixels in a photo
- Computers in a network
- Friends in a social network
- Transistors in a chip
- Elements in a math set
- Variable names in Fortran language
- Metallic side in a composite system 

-> supress details: simply use integers (indexes).

**"is connected to"**
- Reflexive: _p_ is connected to _p_
- Symmetric: if _p_ is connected to _q_, then _q_ is connected to _p_
- Transitive: if(p-q,q-r) then p-r

Max set of connected components

```java
public class QuickFindUF
{
    private int[] id;

    public QuickFindUF(int N)
    {
        id = new int[N];
        for(int i = 0; i<N; i++)
        {
            id[i] = i;
        }
    }

    public boolean connected(int p, int q)
    {
        return id[p] == id[q];
    }

    public void union(int p, int q)
    {
        int pid = id[p];
        int qid = id[q];
        for (int i = 0; i < id.length; i++)
        {
            if(id[i] == pid) id[i] = qid;
        }
    }
}
```

### quick find

### quick union

- Each element of id 

```java
public class QuickFindUF
{
    private int[] id;

    public QuickFindUF(int N)
    {
        id = new int[N];
        for(int i = 0; i < N; i++)
        {
            // set id element of each object to itself
            // ( N Array accesses )
            id[i] = i;
        }
    }

    private int root(int i)
    {
        // chase parent pointers until reach root
        // ( depth of i array accesses)
        while(i != id[i]) i = id[i];
        return i;
    }
    
    public boolean connected(int p, int q)
    {
        // check if p and q have same root
        // (depth of p and q array accesses)
        return root(p) == root(q);    
    }
    
    public void union(int p, int q)
    {
        // change root of p to point to root of q
        // (depth of p and q array accesses)
        int i = root(p);
        int j = root(q);
        id[i] = j;
    } 
}
```

### improvements

**Improvement 1:**
Weghted quick-union.
 - Modify quick-union to avoid tall trees.
 - Keep track of size of each tree (number of objects).
 - Balance by linking root of smaller tree to root of larger tree.
Avoid putting the large tree lower


Algorithm | initialize | Union  |   Connected
----------|------------|--------|-------------
 quick-find  | N | N | 1
 quick-union | N | N*| N
 weighted QU | N | **lg N** * | lg N

* including cost of finfing roots

### applications

 