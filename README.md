# CH32V003 Blinky in Rust

I could not find a small and simple blinky example for CH32V003 and probe-rs, so here it is!

## Hardware

I used CH32V003F4P6-EVT-R0 and WCH-LinkE. The project is set up for CH32V003F4P6 but should work with any other CH32V chip as well, just change it in `Cargo.toml` and `.cargo/config.toml`. The WCH-Link is detected automatically by probe-rs.

### Connections
On CH32V003F4P6-EVT-R0, connect `PD6` to `LED1`.

Between CH32V003F4P6-EVT-R0 and WCH-LinkE, connect:

`VCC` to `3V3`<br>
`GND` to `GND`<br>
`PD1` to `SWDIO/TMS`


## Running

1. Install Rust and then probe-rs:
```shell
cargo install probe-rs-tools
```

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

4. Connect board and run with
```shell
cargo run
```
or to run with the cargo-embed environment installed with probe-rs:

```shell
cargo embed
```

5. To open a debug environment in VSCode, add this to a launch.json file:
```
{
    "type": "probe-rs-debug",
    "request": "launch",
    "name": "probe-rs ch32",
    "cwd": "${workspaceFolder}",
    "connectUnderReset": false,
    "chip": "CH32V003",
    "flashingConfig": {
        "flashingEnabled": true,
        "haltAfterReset": true
    },
    "probe": "1a86:8010",
    "coreConfigs": [
        {
            "coreIndex": 0,
            "programBinary": "./target/riscv32ec-unknown-none-elf/debug/${workspaceFolderBasename}"
        }
    ]
}
```

## Acknowledgements

This was based on the examples project in `ch32-hal`. You can find the original code here:

https://github.com/ch32-rs/ch32-hal/tree/main/examples/ch32v003