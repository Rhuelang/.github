<div align="center">
  <img src="https://raw.githubusercontent.com/rhuelang/rhue/main/assets/Logo.svg" width="160" alt="Rhue logo">
  <h1>Rhue</h1>
  <p>Luau-style scripting for Rust, compiled to <b>register bytecode</b>.</p>
  <p>
    <a href="https://crates.io/crates/rhue"><img src="https://img.shields.io/crates/v/rhue?style=for-the-badge&amp;color=e07b4f" alt="rhue on crates.io"></a>
    <a href="https://docs.rs/rhue"><img src="https://img.shields.io/docsrs/rhue?style=for-the-badge" alt="docs.rs"></a>
    <a href="https://rhue.dev"><img src="https://img.shields.io/badge/site-rhue.dev-e07b4f?style=for-the-badge" alt="rhue.dev"></a>
  </p>
</div>

Rhue is what you get when you want Luau inside a Rust program. Same syntax, same `--!strict` gradual typing, embeds about as easily as Rhai, and it all compiles to register bytecode for its own VM.

```rust
use rhue::Engine;

fn main() -> Result<(), rhue::Error> {
    let mut engine = Engine::new();
    engine.register("shout", |s: String| s.to_uppercase() + "!");

    let out: String = engine.eval_as(r#"return shout("hello from rhue")"#)?;
    println!("{out}"); // HELLO FROM RHUE!
    Ok(())
}
```

## What's in here

- **[rhue](https://github.com/rhuelang/rhue)** — the language itself. Compiler, VM, type checker, the `rhue` CLI, a language server and a debug adapter
- **[rhue-site](https://github.com/rhuelang/rhue-site)** — [rhue.dev](https://rhue.dev). It doesn't keep its own docs, it pulls them out of the rhue repo every build

Docs are on [rhue.dev](https://rhue.dev) and [docs.rs](https://docs.rs/rhue). Bugs and ideas go in [rhue's issues](https://github.com/rhuelang/rhue/issues).
