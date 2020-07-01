read line, read integer and print
```ocaml
(* 
 * https://atcoder.jp/contests/abc041/tasks/abc041_a
 * *)
let s = read_line()
let i = read_int()

let _ = Printf.printf "%c\n" (s.[i-1])
```

operator overwriting
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

read input and pass it to a function
```ocaml
(*
 * https://atcoder.jp/contests/abc170/tasks/abc170_a
 * *)
open Printf
open Scanf

let solve a b c d e = 15 - a - b - c - d - e

let main =
    scanf "%d %d %d %d %d" solve |> printf "%d\n"
```

init array, for, if
```ocaml
(*
 * https://atcoder.jp/contests/abc170/tasks/abc170_a
 * *)
open Printf
open Scanf

let main =
    let xs = Array.init 5 @@ fun _ -> scanf"%d " @@ fun x -> x in
    for i = 0 to 4 do
        if xs.(i) = 0 then
            printf "%d\n" @@ i + 1
    done
```

double for using Arrays and folds
```ocaml
(*
 * https://atcoder.jp/contests/abc143/tasks/abc143_b
 * *)
Scanf.scanf "%d\n" @@ fun n ->
    let d = Array.init n @@ fun _ -> Scanf.scanf "%d " @@ fun d -yt> d in
    Printf.printf "%d\n" @@
    Array.fold_left (Array.fold_left ( + )) 0 @@
    Array.init n @@ fun i ->
        Array.init n @@ fun j ->
            if i <= j then 0
            else d.(i) * d.(j)
```

Sorting an array
```ocaml
Array.sort (-) my_array;
```
