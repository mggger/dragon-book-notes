## 6.3.1

```
float x ;
record {float x; float y} p;
record {int tag; float x; float y;} q;
```

解答:

SDT
```
S ->                {top = new Env(); offset = 0;}              
    D

D -> T id;          {top.put(id.lexme, T.type, offset); offset += T.width}
    D1


D -> ε     
T -> int            {T.type = interger; T.width = 4}
T -> float          {T.type = float; T.width = 8}

T -> record '{'     {Evn.push(top), top = new Evn(); Stack.push(offset), offset = 0;}

    D '}'           {T.type = record(top); T.width = offset; top = Evn.top(); offset = Stack.pop();}
```

```
line    id      type    offset      Evn

1)      x       float    0          1

2)      x       float    0          2

2)      y       float    8          2

2)      p       record   8          1

3)      tag     int      0          3

3)      x       float    4          3

3)      y       float    12         3

3)      q       record() 24         1  
```