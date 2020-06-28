read line, read integer and print
```ocaml
(* 
 * https://atcoder.jp/contests/abc041/tasks/abc041_a
 * *)
let s = read_line()
let i = read_int()

let _ = Printf.printf "%c\n" (s.[i-1])
```

operator overloading
```ocaml
(* 
 * https://atcoder.jp/contests/abc041/tasks/abc041_b
 * *)
let ( * ) a b = (a * b) mod 1000000007

let () = Scanf.scanf "%d %d %d" (fun a b c ->
    Printf.printf "%d\n" (a*b*c))
```

read n then n space separated integers, sort and apply a function
```ocaml
(* 
 * https://atcoder.jp/contests/abc041/tasks/abc041_c
 * *)
Scanf.scanf "%d" (fun n ->
    let a = Array.init n (fun i -> Scanf.scanf " %d" (fun a -> -a, i+1)) in
    Array.sort compare a;
    Array.iter (fun (_, y) -> Printf.printf "%d\n" y) a
)
```

