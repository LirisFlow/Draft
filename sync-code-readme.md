# sync-code

[![Crates.io](https://img.shields.io/crates/v/sync-code.svg)](https://crates.io/crates/sync-code)
[![Docs.rs](https://docs.rs/sync-code/badge.svg)](https://docs.rs/sync-code)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE)

Synchronize code blocks between different files.

**sync-code** is a preprocessing tool that replaces annotated comments with reusable code during compilation.  
It serves as a clearer alternative to macros in certain scenarios. For example, when code is not heavily duplicated but the design is relatively complex (such as involving generics), using sync-code instead of macros provides much better readability and easier maintenance.  

Unlike macros, sync-code preserves IDE features such as **Go-to-definition** and intelligent auto-completion, ensuring a smoother developer experience.


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
