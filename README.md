# tracing-libatrace

Instrument your application with [tracing](https://github.com/tokio-rs/tracing) and [libatrace](https://github.com/Grainspring/libatrace), and get stack view of your application activity with timing
information using chrome browser:

![rustc typeck_fn tracing](http://grainspring.github.io/imgs/tracing.rustc.typeck_fn.png)

![rustc borrowck tracing](http://grainspring.github.io/imgs/tracing.rustc.mir_borrowck.png)

## Setup

After instrumenting your app with
[tracing](https://github.com/tokio-rs/tracing), add this subscriber like this:

```rust
let subscriber = tracing_subscriber::Registry::default().with(tracing_libatrace::layer().unwrap());
tracing::subscriber::set_global_default(subscriber).unwrap();
```
## Other
when running your application, you must run [tracing atrace](https://github.com/Grainspring/tracing-atrace) standalone to capture tracing log output,

and then open chrome browser with url chrome://tracing/ to load tracing log and view your application activity with timing and callstack.

