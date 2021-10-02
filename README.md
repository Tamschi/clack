# clack

[![Lib.rs](https://img.shields.io/badge/Lib.rs-*-84f)](https://lib.rs/crates/clack)
[![Crates.io](https://img.shields.io/crates/v/clack)](https://crates.io/crates/clack)
[![Docs.rs](https://docs.rs/clack/badge.svg)](https://docs.rs/clack)

![Rust 1.51](https://img.shields.io/static/v1?logo=Rust&label=&message=1.51&color=grey)
[![CI](https://github.com/Tamschi/clack/workflows/CI/badge.svg?branch=develop)](https://github.com/Tamschi/clack/actions?query=workflow%3ACI+branch%3Adevelop)
![Crates.io - License](https://img.shields.io/crates/l/clack/0.0.1)

[![GitHub](https://img.shields.io/static/v1?logo=GitHub&label=&message=%20&color=grey)](https://github.com/Tamschi/clack)
[![open issues](https://img.shields.io/github/issues-raw/Tamschi/clack)](https://github.com/Tamschi/clack/issues)
[![open pull requests](https://img.shields.io/github/issues-pr-raw/Tamschi/clack)](https://github.com/Tamschi/clack/pulls)
[![good first issues](https://img.shields.io/github/issues-raw/Tamschi/clack/good%20first%20issue?label=good+first+issues)](https://github.com/Tamschi/clack/contribute)

[![crev reviews](https://web.crev.dev/rust-reviews/badge/crev_count/clack.svg)](https://web.crev.dev/rust-reviews/crate/clack/)

A scoped signal forwarder.

Current operating system support: Unix (via the `nix` crate).

## Installation

Please use [cargo-edit](https://crates.io/crates/cargo-edit) to always add the latest version of this library:

```cmd
# cargo add clack # Reserved by another developer.
```

## Example

```rust
let mut child = std::process::Command
  ::new("ping")
  .args(["example.com", "-c", "3"])
  .spawn().unwrap();

{
  let _relay_guard = clack::Intent::InterruptFromKeyboard.relay_to_child(&child); // <--
  child.wait().ok(); // Press Ctrl-c about here.
}

println!("Still alive!");
```

## License

Licensed under either of

- Apache License, Version 2.0
   ([LICENSE-APACHE](LICENSE-APACHE) or <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT license
   ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

See [CONTRIBUTING](CONTRIBUTING.md) for more information.

### Interactive Testing

Run

```bash
cargo run --all-features
```

or

```bash
cargo run --all-features -- -r
```

and press (with `-r`/`--recursive` repeatedly Enter and then) Ctrl+c.

The program should exit gracefully.

## [Code of Conduct](CODE_OF_CONDUCT.md)

## [Changelog](CHANGELOG.md)

## Versioning

`clack` strictly follows [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html) with the following exceptions:

- The minor version will not reset to 0 on major version changes (except for v1).  
Consider it the global feature level.
- The patch version will not reset to 0 on major or minor version changes (except for v0.1 and v1).  
Consider it the global patch level.

This includes the Rust version requirement specified above.  
Earlier Rust versions may be compatible, but this can change with minor or patch releases.

Which versions are affected by features and patches can be determined from the respective headings in [CHANGELOG.md](CHANGELOG.md).
