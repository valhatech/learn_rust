
# Créer la bibliothèque Rust

Dans le dossier du projet :

```bash
cd C:\Users\Admin\Documents\godot-rust-demo
cargo new rust --lib
```

Structure :

```bash
godot_rust_demo/
├── rust/
│   ├── Cargo.toml
│   └── src/
│       └── lib.rs
```

# Configurer Cargo.toml

Ouvrez :

rust/Cargo.toml

Remplacez le contenu par :

```TOM
[package]
name = "godot_rust_demo"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
godot = "0.2"

[profile.dev]
opt-level = 0

[profile.release]
opt-level = 3
```
