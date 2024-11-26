# The Rust Embedded C book

Starting this project up by installing Rust using the [Embedded C book instructions](https://docs.rust-embedded.org/book/intro/install.html).

Steps were (as of 2024-11-26) for x86-64 darwin...

```sh
# rustup
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# fish shell only
source ~/.cargo/env.fish

# check version
rustc -V
```

My implementation will implement the [specific FatFS drivers](http://elm-chan.org/fsw/ff/doc/appnote.html#port) targeting ARMv8
but I want to support most microcontroller uses. Still, for now:

```sh
# Cortex-M23 (ARMv8-M architecture):
# Cortex-M33 and M35P (ARMv8-M architecture):
# Cortex-M33F and M35PF with hardware floating point (ARMv8-M architecture):

rustup target add thumbv8m.base-none-eabi
rustup target add thumbv8m.main-none-eabi
rustup target add thumbv8m.main-none-eabihf
```

Need `llvm-tools`

```sh
cargo install cargo-binutils
rustup component add llvm-tools
```
TODO: why?

Finally, for generating projects:

```sh
cargo install cargo-generate
```

Next on the list for macOS specifically:

```sh
brew install arm-none-eabi-gdb openocd qemu
```

Onchip debugger sounds cool, and qemu is an emulator.

# Testing a board connection

I don't have the board yet, but let's write this here for reference:

```sh
openocd -f interface/stlink.cfg -f target/stm32f3x.cfg
```
