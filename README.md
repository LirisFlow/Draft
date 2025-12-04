# stm32f1-hal

[![Crates.io](https://img.shields.io/crates/v/stm32f1-hal.svg)](https://crates.io/crates/stm32f1-hal)
[![Docs.rs](https://docs.rs/stm32f1-hal/badge.svg)](https://docs.rs/stm32f1-hal)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE)
[![Downloads](https://img.shields.io/crates/d/stm32f1-hal.svg)](https://crates.io/crates/stm32f1-hal)

**stm32f1-hal** is a Rust Hardware Abstraction Layer (HAL) for **STM32F1 microcontrollers** (STM32F103, STM32F107, etc.), built on [`embedded-hal`](https://github.com/rust-embedded/embedded-hal), designed for **embedded development**.  
This crate provides a safe, idiomatic, and easy-to-use interface for developers who want to explore Rust on STM32F1 devices.

## 🎯 Motivation
The existing crates did not fully meet my needs:  
- **stm32f1xx-hal** has a design that I found unsuitable for my workflow.  
- **stm32-hal** does not support the STM32F1 series at all.  

For these reasons, I decided to create a new crate — **stm32f1-hal**.  
Many parts of the implementation are adapted from `stm32f1xx-hal`, but the overall design is focused on clarity and usability.

## 📖 Design Philosophy
The guiding principles behind this project are:

- **Readability first**: prioritize clear, idiomatic Rust code.  
- **Safety**: leverage Rust’s type system to prevent misuse.  
- **Consistency**: follow `embedded-hal` traits for portability.  
- **Extensibility**: easy to add new peripherals and features.  

In addition, some practical choices shape the implementation:

- **Avoiding unnecessary complexity**: macros and heavy generics are avoided in complex modules, since they often obscure the logic.  
- **Sync-code for duplication**: shared code across peripherals is managed with *sync-code*.  
- **Automated generation**: a script is used to generate GPIO alternate function remapping code.  

## 📌 Project Status
This project is still in its early stages, with only a few features implemented so far.  
Contributions and feedback are welcome to help expand support for more peripherals and STM32F1 variants.

## ✨ Features
- GPIO (input/output, alternate functions)
- Timers (basic usage, PWM)
- UART (serial communication)
- SPI (basic support)
- Extensible design for future peripherals (I2C, ADC, DMA)
  
## 📦 Installation
```text
# Installation
cargo add stm32f1-hal

# Cargo.toml Configuration
[dependencies]
stm32f1-hal = "0.1"
```
## 🚀 Quick Start Example
More usage examples can be found in the [examples](./examples) directory.

```text
use stm32f1_hal as hal;
use hal::pac;
use hal::prelude::*;

fn main() {
    let dp = pac::Peripherals::take().unwrap();
    let mut flash = dp.FLASH.constrain();
    let mut rcc = dp.RCC.constrain();

    let clocks = rcc.cfgr.freeze(&mut flash.acr);
    let mut gpioa = dp.GPIOA.split(&mut rcc.apb2);

    let mut led = gpioa.pa5.into_push_pull_output(&mut gpioa.crl);

    loop {
        led.set_high();
        // delay...
        led.set_low();
        // delay...
    }
}
```

## 🧩 Supported Devices
- STM32F103 (Blue Pill, Black Pill boards)
- STM32F107 (Ethernet-enabled variants)
- More STM32F1 family devices planned

## 🛠 Contributing
Contributions are welcome!  
- Open issues for bugs or feature requests.  
- Submit PRs with improvements or new peripheral support (I2C, ADC, DMA, etc.).  
- Follow Rust Embedded community guidelines.  
- Join discussions in the [Rust Embedded Matrix Chat](https://matrix.to/#/#rust-embedded:matrix.org).

## 🗺 Roadmap
- [ ] I2C support
- [ ] ADC support
- [ ] DMA integration
- [ ] More STM32F1 variants

## 🌍 Community & Resources
- Rust Embedded Book
- STM32F1 Reference Manual
- Rust Embedded Matrix Chat

## 📜 License
This project is licensed under either of the following at your option:
- [MIT License](./LICENSE)
- [Apache License (Version 2.0)](./LICENSE)

## 🔖 Keywords
**stm32 · stm32f1 · rust · embedded-hal · microcontroller · embedded development**
