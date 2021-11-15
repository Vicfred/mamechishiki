read and unpack integers
```nim
var n,m : int
(n,m) = stdin.readLine.split.map(parseInt)
```

read int
```nim
import strutils
let rating = stdin.readLine.parseInt
```

read list of space separated integers
```nim
import strutils, sequtils
let line = stdin.readLine.split.map(parseInt)
```
or
```nim
let get = iterator: string {.closure.} =
  for s in stdin.readAll.split: yield s
```

initialize list of integers
```nim
var snukes = newSeq[int](n);
```

max of more than 2 numbers
```nim
max(@[6,5,4,3,2,21,4,5,])
```

create an array containing 1..n
```nim
var ini = (1..n).toSeq
```

initialize NxM matrix
```nim
import sugar
var a = newSeq[seq[int]](n).map(x => newSeq[int](m))
```
or
```nim
var a = newSeqWith(n, newSeq[int](m))
```

read a NxM matrix
```nim
let A = (1..n).mapIt(stdin.readLine.split.map(parseInt))
```

empty tree
```nim
var tree = newSeq[seq[edge]](n+1)
```

read input
```nim
import strutils, sequtils

let read = iterator: string {.closure.} =
  while true:
    for s in stdin.readLine.split:
      yield s
```

print an iterable separated with spaces
```nim
echo b.mapIt($it).join(" ")
```

read n lines
```nim
let lines = (1 .. n).mapIt(stdin.readLine)
```

read n lines
```nim
let lines = newSeqWith(n, stdin.readline)
```

operator overloading
```nim
proc `*`(s: string, n: int): string =
  result = ""
  for _ in 1..n:
    result &= s

echo "a" * 5 # It works

echo 5 * 5 # The default implementation stills working
echo 45 * 89
```

misc
```nim
"hello" & "world" # string concatenation
$type             #convert type to string
inc x             # x++
stdout.write      # echo with no \n
fmt"X es {x}"     # python f-strings style
toSet()           # convert to set
a.sort system.cmp # 0.13.0 needs a sorting function
```

table with character frequency
```nim
import tables
var letters = toCountTable(myString)
 
# 0.13.0
import tables
var letters = initCountTable[char]()
for c in myString:
  letters.inc(c)
  
let groups = {"1": 1, "3": 1, "5": 1, "7": 1, "8": 1, "10": 1, "12": 1,
              "4": 2, "6": 2, "9": 2, "11": 2,
              "2": 3}.toTable
```

switch/case
```nim
case x:
  of 3: echo "X is a 3"
  of 5: echo "X is a 5"
  of 1:
    inc x
    echo "X where a 1 but now is 2"
  else: echo "I don't know what is X"
```
print depending on a conditional
```nim
echo(if conditional: "Yes" else: "No")
```

unpack variables

https://github.com/Yardanico/nim-snippets/blob/master/unpack_macro.nim

operator overloading
```nim
type Restaurant = object
  name: string
  score: int
  id: int;

proc cmp(x, y: Restaurant): int =
  if x.name == y.name:
    return -cmp(x.score, y.score)
  return cmp(x.name, y.name)
```

implement math-like notation for comparison using a macro
```nim
import macros

proc processBool(n: NimNode): NimNode =
  echo n.treeRepr
  result = copyNimTree n
  expectKind(n, nnkInfix)
  var id: NimNode
  case n[1].kind
  of nnkInfix:
    id = n[1][2]
    result[1] = id
    result = nnkInfix.newTree(ident("and"), result)
    result.add n[1]
    result = newStmtList(result)
    echo result.treerepr
  else: discard

macro `{}`(x, y: untyped): untyped =
  if x.strVal == "eq":
    result = processBool(y)

let x = 6
let a = 2
let b = 2
echo eq{ 4 < x <= 10 }
echo eq{ 8 < x < 10 }
echo eq{ a == b == 2 }
echo eq{ 1 < a != 2 }
```

