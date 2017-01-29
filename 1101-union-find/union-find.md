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
        for (int i = 0; i < id.lenght; i++)
        {
            if(id[i] == pid) id[i] = qid;
        }
    }
}
```

### quick find

### quick union
### improvements
### applications

 