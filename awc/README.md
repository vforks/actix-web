# awc (Actix Web Client)

> Async HTTP and WebSocket client library.

[![crates.io](https://img.shields.io/crates/v/awc?label=latest)](https://crates.io/crates/awc)
[![Documentation](https://docs.rs/awc/badge.svg?version=2.0.1)](https://docs.rs/awc/2.0.1)
![Apache 2.0 or MIT licensed](https://img.shields.io/crates/l/awc)
[![Dependency Status](https://deps.rs/crate/awc/2.0.1/status.svg)](https://deps.rs/crate/awc/2.0.1)
[![Join the chat at https://gitter.im/actix/actix-web](https://badges.gitter.im/actix/actix-web.svg)](https://gitter.im/actix/actix-web?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Documentation & Resources

- [API Documentation](https://docs.rs/awc/2.0.1)
- [Example Project](https://github.com/actix/examples/tree/HEAD/awc_https)
- [Chat on Gitter](https://gitter.im/actix/actix-web)
- Minimum Supported Rust Version (MSRV): 1.42.0

## Example

```rust
use actix_rt::System;
use awc::Client;
use futures::future::{Future, lazy};

fn main() {
    System::new("test").block_on(lazy(|| {
       let mut client = Client::default();

       client.get("http://www.rust-lang.org") // <- Create request builder
          .header("User-Agent", "Actix-web")
          .send()                             // <- Send http request
          .and_then(|response| {              // <- server http response
               println!("Response: {:?}", response);
               Ok(())
          })
    }));
}
```
