# sync-code

[![Crates.io](https://img.shields.io/crates/v/sync-code.svg)](https://crates.io/crates/sync-code)
[![Docs.rs](https://docs.rs/sync-code/badge.svg)](https://docs.rs/sync-code)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE)

**sync-code** is a Rust tool for managing and synchronizing duplicate code across modules and peripherals.  
It was created to solve a common problem in embedded development: macros and heavy generics often reduce readability, making maintenance harder.  
Instead, sync-code provides a clear, script-driven approach to keep code consistent and easy to understand.

## 🎯 Motivation
In embedded Rust projects, especially HALs, code duplication is inevitable.  
Existing solutions rely heavily on macros or generics, which may shorten code but often obscure its meaning.  
**sync-code** was designed to prioritize **readability and maintainability**: code should be easy to read, review, and extend.

## ✨ Features
- Synchronize duplicate code across multiple modules.  
- Script-based generation for GPIO alternate function remapping.  
- Avoid complex macro/generic patterns that reduce clarity.  
- Lightweight and easy to integrate into existing projects.  

## 📖 Design Philosophy
- **Readability first**: code is read far more often than it is written.  
- **Concise ≠ simple**: fewer lines don’t always mean easier to understand.  
- **Practical automation**: use scripts to handle repetitive patterns instead of hiding them in macros.  
- **Maintainability**: prioritize long-term clarity over short-term brevity.  

## 📦 Installation
```bash
cargo add sync-code
```
