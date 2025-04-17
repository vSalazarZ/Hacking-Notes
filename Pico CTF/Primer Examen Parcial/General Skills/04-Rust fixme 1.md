## Descripción 
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).

Hint:
1. Cargo is Rust's package manager and will make your life easier. See the getting started page [here](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html)
2. [println!](https://doc.rust-lang.org/std/macro.println.html)
3. Rust has some pretty great compiler error messages. Read them maybe?
## Solución 1

Descargamos el Rust. Descargamos y descomprimimos el archivo del reto. Luego editamos el archivo main.rs para corregir los errores de sintaxis en Rust, agregando la función main y usando println! correctamente para que imprimiera la flag.

```
Estos son los comandos que utilicé 

omarsalazar@DESKTOP-H97NF1C:~$ wget https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
omarsalazar@DESKTOP-H97NF1C:~$ ls
omarsalazar@DESKTOP-H97NF1C:~$ tar -xzvf fixme1.tar.gz
omarsalazar@DESKTOP-H97NF1C:~$ wget https://doc.rust-lang.org/book/ch01-03-hello-cargo.html
omarsalazar@DESKTOP-H97NF1C:~$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
omarsalazar@DESKTOP-H97NF1C:~$ source $HOME/.cargo/env
omarsalazar@DESKTOP-H97NF1C:~$ nano archivo_rust.rs
use xor_cryptor::XORCryptor;

fn main() {
    // Key for decryption
    let key = String::from("CSUCKS"); // How do we end statements in Rust?

    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", ">
    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!(
        "{}:?", // How do we print out a variable in the println function?
        String::from_utf8_lossy(&decrypted_buffer)
omarsalazar@DESKTOP-H97NF1C:~$ cargo build
omarsalazar@DESKTOP-H97NF1C:~$ cd fixme1
omarsalazar@DESKTOP-H97NF1C:~/fixme1$ cat main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme1$ nano main.rs
omarsalazar@DESKTOP-H97NF1C:~/fixme1$ cargo build
omarsalazar@DESKTOP-H97NF1C:~/fixme1$ cargo build
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.00s
     Running `/home/omarsalazar/fixme1/target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}:?
omarsalazar@DESKTOP-H97NF1C:~/fixme1/src$

flag: picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}
```
