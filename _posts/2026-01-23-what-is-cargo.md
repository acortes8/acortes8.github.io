---
title: What is Rust's Cargo?
date: 2026-01-21
categories: [Learning, Guides]
tags: [rust, cargo, guides, learning]
---

To understand Cargo, we should first see what using Rust without Cargo looks like.

## A basic Rust program without Cargo
To start we'll make a Rust file in an empty directory. Rust files end in the `.rs` extension. We'll name this file `main`, and also populate the file with a short code snippet.

`main.rs`:
```rust
fn main() {
    println!("Hello, world!");
}
```

To compile this Rust program we'll  run `$ rustc main.rs` in the terminal. 

Remember terminal notation, the '$' symbol denotes a line you enter into your terminal, not including the symbol itself. A '>' symbol denotes terminal output. 

After compilation is completed, Rust will create a new executable file that will appear in the directory as a file named `main` with no file type extension. You can run this executable by running the command `$ ./main` in your terminal.

A benefit of a compiled language like Rust is that you can run this executable file on another computer without having to have Rust installed. Compare this to interpreted languages like Ruby or Python where you do need to have them installed to be able to run their program files. This is because Rust compiles its programs into a binary executable that will readily run on most computers. 

These are the basics of a Rust program without Cargo, so now let's look at the basics of one with Cargo.

## A basic Rust program with Cargo

Cargo is Rust's build system and package manager, if you're familiar with `UV` for Python, it is a very similar system. 

Cargo gives you the tools for building your code and dependencies. It comes installed with most Rust installations, you can check if you have it by running `cargo --version`.

To get started with our Rust program, we create a new 'project' with Cargo. To do this we run the command `$ cargo new hello_cargo`. This command will create a new directory for your `hello_cargo` project that you can `$ cd` into.

You will see that Cargo generated two things inside this directory. It generated a `cargo.toml` file, and a `src` directory. It also initializes a new Git repository for you.

The `cargo.toml` file will look something like this:
```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2024"

[dependencies]
```

This is where project's version information and dependencies are listed. 

In the `src` directory you will see that Cargo generated a `main.rs` file for you, with a snippet of code identical to the one we used as an example before. Your source files will all live in this `src` directory, the top-level project directory is where you should put your README files, license information, configuration files, and other non-code files. 

### Compiling and running programs with Cargo
Instead of using `rustc` to compile your program, we can use `$ cargo build`. Simply run that command in the top-level project directory and it will compile your program into the binary executable, placing it in the newly generated `./target/debug/` directory.

You can then run your executable by running `$ ./target/debug/hello_cargo` in the terminal.

However, instead of doing two separate steps you use a command that combines them into one: `$ cargo run`. It is more convenient so most people opt for this combined command. 

If your program was already compiled previously, and nothing has changed, `$ cargo run` will skip compilation and just run the program instead to be efficient. If there are some changes in the source files made, it can tell and will recompile the program.

If you just want check that your code can compile, without actually generating an executable file you may run the `$ cargo check` command. This is good for checking your work intermittently without generating the binary executable each time.

### Compiling for release
You might've wondered why Cargo generates the executable file in a debug directory when running `$ cargo build`. That is because that version of the program is a development version that compiles quicker but at the cost of some performance in the final file.

When your program is in a more complete state where you want all the performance Rust comes with, then you want to build the release version of your program. The compilation for this version takes longer as the compiler does additional optimization tasks. You can compile this version with the `$ cargo build --release` command, and it will generate that new executable in the `./target/release/` directory.

## Converting a non-Cargo Rust program to a Cargo managed Rust program
If you have a Rust program that doesn't use Cargo but would now like to use Cargo, converting over is easy.

Simply create a directory for your project, then a `src` subdirectory inside it. Move your Rust files into that `src` subdirectory. Then in the top-level project directory run `$ cargo init`, this will create a `cargo.toml` for you. That's all there is to it.