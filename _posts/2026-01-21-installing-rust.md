---
title: Installing Rust (MacOS)
date: 2026-01-21
categories: [Learning, Guides]
tags: [mac, rust, rustup, guides, learning, installing]
---

## Installation
To install Rust we'll make use of `rustup`, a command line tool for managing Rust and its tools.

1. Open the terminal and enter the following command:
   ```shell
   $ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
   ```
2. You will be prompted in the terminal to choose between three different installation options:
   ```shell
   Current installation options:
   
   ...
   
   1) Proceed with standard installation (default - just press enter)
   2) Customize installation
   3) Cancel installation
   ```
   Simply press the `enter` key to proceed with the standard installation, if you don't need to customize the installation.
4. The installer will continue on and you should get a line in the terminal towards the end that says `Rust is installed now. Great!`. You will also get a line that says `To get started you may need to restart your current shell`. That is a common step with installations and it's purpose is to refresh your environment so changes made by the installer can take affect. Feel free to restart your terminal now to do so.
5. Rust should now be installed. However, Rust requires a `linker` as well. A `linker` is a program that allows Rust to join its complied outputs into one file. It is likely that your system already has a `linker`, but if you get linker errors then go ahead and install one. You can install a `linker` by installing a C complier, as they typically include one. On macOS, run the following command to install a C complier:
   ```shell
   $ xcode-select --install
   ```
6. To ensure you installed Rust correctly, run `rustc --version` in your terminal. If you see something like `rustc 1.92.0 (ded5c06cf 2025-12-08)` then you've successfully installed Rust.

## Updating Rust
To update Rust, simply run the following command: `rustup update`.

## Accessing documentation locally
To access the Rust docs locally, run the following command: `rustup doc`.