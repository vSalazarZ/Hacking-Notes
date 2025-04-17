## Descripción 
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).

Hint:
1. https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html
## Solución 1

Descargamos el archivo del reto y lo descomprimimos. Intentamos compilarlo pero apareció un error porque el programa intentaba modificar una variable que no era mutable. Editamos el archivo principal para hacer los cambios necesarios, convertimos la variable en mutable y también cambiamos la función para que pudiera recibirla. Volvemos a compilar el programa nos da la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz
--2025-04-15 22:25:29--  https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 65.9.149.59, 65.9.149.85, 65.9.149.24, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|65.9.149.59|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1585 (1.5K) [application/octet-stream]
Saving to: ‘fixme2.tar.gz’

fixme2.tar.gz                 100%[=================================================>]   1.55K  --.-KB/s    in 0s

2025-04-15 22:25:30 (361 MB/s) - ‘fixme2.tar.gz’ saved [1585/1585]

omarsalazar@DESKTOP-H97NF1C:~$ ls
fixme2.tar.gz
omarsalazar@DESKTOP-H97NF1C:~$ tar -xzvf fixme2.tar.gz
fixme2/
fixme2/Cargo.toml
fixme2/Cargo.lock
fixme2/src/
fixme2/src/main.rs
omarsalazar@DESKTOP-H97NF1C:~$ cd fixme2
omarsalazar@DESKTOP-H97NF1C:~/fixme2$ ls
Cargo.lock  Cargo.toml  src
omarsalazar@DESKTOP-H97NF1C:~/fixme2$ cd src
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ main.rs
main.rs: command not found
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/omarsalazar/fixme2)
error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
 --> src/main.rs:9:5
  |
9 |     borrowed_string.push_str("PARTY FOUL! Here is your flag: ");
  |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
  |
help: consider changing this to be a mutable reference
  |
3 | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
  |                                                        +++

error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
  --> src/main.rs:20:5
   |
20 |     borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
   |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
   |
help: consider changing this to be a mutable reference
   |
3  | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
   |                                                        +++

For more information about this error, try `rustc --explain E0596`.
error: could not compile `rust_proj` (bin "rust_proj") due to 2 previous errors
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cd src
-bash: cd: src: No such file or directory
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ main.rs
main.rs: command not found
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ nano main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo build
   Compiling rust_proj v0.1.0 (/home/omarsalazar/fixme2)
error[E0308]: mismatched types
  --> src/main.rs:35:31
   |
35 |     decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it ...
   |     -------                   ^^^^^^^^^^^ types differ in mutability
   |     |
   |     arguments to this function are incorrect
   |
   = note: expected mutable reference `&mut String`
                      found reference `&String`
note: function defined here
  --> src/main.rs:3:4
   |
3  | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that ...
   |    ^^^^^^^                           ----------------------------

For more information about this error, try `rustc --explain E0308`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ nano main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo build
   Compiling rust_proj v0.1.0 (/home/omarsalazar/fixme2)
error[E0308]: mismatched types
  --> src/main.rs:35:31
   |
35 |     decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it ...
   |     -------                   ^^^^^^^^^^^ types differ in mutability
   |     |
   |     arguments to this function are incorrect
   |
   = note: expected mutable reference `&mut String`
                      found reference `&String`
note: function defined here
  --> src/main.rs:3:4
   |
3  | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that ...
   |    ^^^^^^^                           ----------------------------

For more information about this error, try `rustc --explain E0308`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ nano main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo build
   Compiling rust_proj v0.1.0 (/home/omarsalazar/fixme2)
error[E0596]: cannot borrow `party_foul` as mutable, as it is not declared as mutable
  --> src/main.rs:35:31
   |
35 |     decrypt(encrypted_buffer, &mut party_foul); // Is this the correct way to pass a value to a function so that...
   |                               ^^^^^^^^^^^^^^^ cannot borrow as mutable
   |
help: consider changing this to be mutable
   |
34 |     let mut party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
   |         +++

For more information about this error, try `rustc --explain E0596`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ nano main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo build
   Compiling rust_proj v0.1.0 (/home/omarsalazar/fixme2)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.37s
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.00s
     Running `/home/omarsalazar/fixme2/target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}
omarsalazar@DESKTOP-H97NF1C:~/fixme2/src$

falg: picoCTF{4r3_y0u_h4v1n5_fun_y31?}
```
