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
    let d = Array.init n @@ fun _ -> Scanf.scanf "%d " @@ fun d -> d in
    Printf.printf "%d\n" @@
    Array.fold_left (Array.fold_left ( + )) 0 @@
    Array.init n @@ fun i ->
        Array.init n @@ fun j ->
            if i <= j then 0
            else d.(i) * d.(j)
```

Sorting an array
```ocaml
(* https://atcoder.jp/contests/abc171/tasks/abc171_b *)

Printf.printf "%d\n" @@
Scanf.scanf "%d %d\n" @@ fun n k ->
    let a = Array.init n @@ fun _ -> Scanf.scanf "%d " @@ fun i -> i in
    Array.sort (-) a;
    let ans = ref 0 in
    for i = 0 to k-1 do
        ans := !ans + a.(i)
    done;
    !ans;;
```

fold example
```ocaml
(* https://atcoder.jp/contests/abc139/tasks/abc139_a *)
let () = Scanf.scanf "%s\n%s" @@ fun s t ->
  Printf.printf "%d\n" @@
  Array.fold_left ( + ) 0 @@
  Array.init 3 @@ fun i -> if s.[i] = t.[i] then 1 else 0
```


fold over 2 arrays
```ocaml
    (* https://atcoder.jp/contests/abc139/tasks/abc139_a *)
    open Batteries
    let s = String.explode (read_line ())
    let t = String.explode (read_line ())
    let ans = List.fold_left2 (fun a b c -> if b = c then a + 1 else a) 0 s t
    let () = print_int ans
```

String.iteri
```ocaml
    (* https://atcoder.jp/contests/abc139/tasks/abc139_a *)
    let s = read_line ()
    let t = read_line ()
    let ans = ref 0
    let _ = String.iteri (fun i c -> if c = t.[i] then incr ans) s; Printf.printf "%d\n" !ans
```

loop from recursion
```ocaml
    (* https://atcoder.jp/contests/abc139/tasks/abc139_a *)
    let () =
        let main () =
            let s = read_line () in
            let t = read_line () in
            let rec loop i acc =
                if i = 3 then acc else
                    loop (i + 1) (acc + if s.[i] = t.[i] then 1 else 0)
            in
            let r = loop 0 0 in
            Printf.printf "%d\n" r
        in
        main ()
```

typical recursion with accumulator and index
```ocaml
(* unihernandez22
 * https://atcoder.jp/contests/abc139/tasks/abc139_a
 * implementation
 * *)
 
let rec count_eq s t i c =
    if i == String.length s then c
    else if s.[i] == t.[i] then count_eq s t (i+1) (c+1)
    else count_eq s t (i+1) c;;
 
Printf.printf "%d\n" @@
Scanf.scanf "%s\n%s\n" @@ fun s t ->
    count_eq s t 0 0;;
```

Pipes
```ocaml
(* https://atcoder.jp/contests/abc077/tasks/abc077_b *)
Scanf.scanf "%f\n" (fun x -> x)
|> sqrt
|> int_of_float
|> (fun x -> x * x)
|> Printf.printf "%d\n"


```
