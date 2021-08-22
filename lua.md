Read integer.

```lua
x = io.read("*n")
```

Read various integers.
```lua
a, b, c, d = io.read("*n", "*n", "*n", "*n")
```

Read string.
```lua
s = io.read()
```

For, if and string at index.
```lua
for i = 1, 3 do
    if s:sub(i,i) == '1' then
        ans = ans + 1
    end
end
```

Various misc operations: list of numbers, modulo, minimum.
```lua
n = io.read("*n")
A = {}
for i = 1,n do
    A[i] = io.read("*n")
end
minima = 2^64
for i = 1,n do
    times = 0
    while math.fmod(A[i],2) == 0 do
        A[i] = A[i]/2
        times = times + 1
    end
    minima = math.min(minima, times)
end
print(minima)
```
