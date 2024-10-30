# CH32V003 Blinky in Rust

I could not find a small and simple blinky example for CH32V003 and probe-rs, so here it is!

1. Install Rust.

2. Set up project to use Rust Nightly
```shell
cd ch32v003-blinky-rust
rustup install nightly
rustup override set nightly
```

3. Install std sources
```shell
rustup component add rust-src
```


## Acknowledgements

This was based on the examples project in `ch32-hal`. You can find the original code here: 

https://github.com/ch32-rs/ch32-hal/tree/main/examples/ch32v003