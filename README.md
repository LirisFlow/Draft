# stm32f1-hal

[![Crates.io](https://img.shields.io/crates/v/stm32f1-hal.svg)](https://crates.io/crates/stm32f1-hal)
[![Docs.rs](https://docs.rs/stm32f1-hal/badge.svg)](https://docs.rs/stm32f1-hal)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE)

**stm32f1-hal** is a Rust Hardware Abstraction Layer (HAL) for **STM32F1 microcontrollers** (STM32F103, STM32F107, etc.), built on [`embedded-hal`](https://github.com/rust-embedded/embedded-hal), designed for **embedded development**.  
This crate provides a safe, idiomatic, and easy-to-use interface for developers who want to explore Rust on STM32F1 devices.

---

## 🎯 Motivation
The purpose of this project is simple: **make STM32F1 development in Rust clear, readable, and approachable**.  
Instead of focusing only on performance or completeness, the design emphasizes **readability first**, leveraging Rust’s type system to ensure safety while keeping code idiomatic and easy to understand.  

By providing a lightweight and consistent HAL, this project aims to lower the barrier for embedded developers exploring Rust on STM32F1 boards like the popular **Blue Pill**.


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

## 📖 Design Philosophy
- Readability first: prioritize clear, idiomatic Rust code.
- Safety: leverage Rust’s type system to prevent misuse.
- Consistency: follow embedded-hal traits for portability.
- Extensibility: easy to add new peripherals and features.

## 🛠 Contributing
- Contributions are welcome!
- Open issues for bugs or feature requests.
- Submit PRs with improvements or new peripheral support.
- Follow Rust Embedded community guidelines.

## 🗺 Roadmap
- [ ] I2C support
- [ ] ADC support
- [ ] DMA integration
- [ ] More STM32F1 variants

## 🌍 Community & Resources
- Rust Embedded Book
- STM32F1 Reference Manual
- Rust Embedded Matrix Chat
