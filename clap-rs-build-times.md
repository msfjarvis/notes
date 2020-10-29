---
date: 2020-10-27T11:53
---

# derive-based argument parsers slow down build

[clap-rs](https://github.com/clap-rs/clap) is an excellent argument parser but build times for it are absolutely abysmal. Here's stats on [healthchecks-rs](https://msfjarvis.dev/g/healthchecks-rs)

```
Benchmark #1: cargo build --release
  Time (mean ± σ):     37.308 s ±  0.403 s    [User: 228.193 s, System: 10.661 s]
  Range (min … max):   36.830 s … 38.054 s    10 runs
```

So I tried to switch to [argh](https://github.com/google/argh), and got these build times.

```
Benchmark #1: cargo build --release
  Time (mean ± σ):     38.430 s ±  0.281 s    [User: 235.046 s, System: 11.600 s]
  Range (min … max):   37.981 s … 38.819 s    10 runs
```

As you can see, it's just as slow if not ever so slightly slower :(
