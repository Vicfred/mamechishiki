read line, read integer and print
```ocaml
let s = read_line()
let i = read_int()

let _ = Printf.printf "%c\n" (s.[i-1])
```

operator overloading
```ocaml
let ( * ) a b = (a * b) mod 1000000007

let () = Scanf.scanf "%d %d %d" (fun a b c ->
    Printf.printf "%d\n" (a*b*c))
```

