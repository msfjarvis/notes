---
date: 2020-10-27T11:53
---

# clap-rs is slow to build

[clap-rs](https://github.com/clap-rs/clap) is an excellent argument parser but build times for it are absolutely abysmal. Here's stats on [healthchecks-rs](https://msfjarvis.dev/g/healthchecks-rs)

![Overall build time for healthchecks-rs](https://pbs.twimg.com/media/ElUOhPgVcAENsLO?format=png&name=900x900)

![Clap's contribution to the build time](https://pbs.twimg.com/media/ElUOrjjUcAAXC_T?format=png&name=medium)

As you can see, clap-rs takes up around **HALF** of the total build time for the binaries. I will be attempting to migrate to [argh](https://github.com/google/argh) in an effort to combat this build overhead and will update this page when I have some numbers.
