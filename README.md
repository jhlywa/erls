ERLS
=====

Manage multiple Erlang installs with per directory configuration.

## Build

```
$ cargo build --release
```

## Install

```
$ mkdir -p ~/.cache/erls/bin
$ cp ./target/release/erls ~/.cache/erls/bin/
$ export PATH=~/.cache/erls/bin:$PATH
```

## Build Erlang

`erls` will create a default config under `~/.config/erls/config` if you don't create it yourself and it'll contain:

```
[erls]
dir=<your home>/.cache/erls

[repos]
default=https://github.com/erlang/otp
```

To list tags available to build one:

```
$ erls tags
...
$ erls build OTP-21.2
```

## Configuring Erlang Compilation

To pass options to `./configure` (like for setting where SSL is in OSX I think) you can add them in the config file:

``` ini
[erls]
default_configure_options=--enable-lock-counter
```

Or pass through the env variable `ERLS_CONFIGURE_OPTIONS`:

``` shellsession
$ ERLS_CONFIGURE_OPTIONS=--enable-lock-counter erls build OTP-21.2
```
