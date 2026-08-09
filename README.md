# homebrew-why

Homebrew tap for [whydatApp](https://github.com/Nostoi/whydatapp) — track *why* you installed every tool on your machine.

## Install

```bash
brew install nostoi/why/why-cli
why init
```

`why init` installs the shell hook and asks before changing anything. Start a new shell afterwards.

## Upgrade

```bash
brew upgrade why-cli
```

Nothing else to do. Schema migrations, new config keys, and the shell hook in `~/.why/` all catch up on the next `why` command; if the hook was refreshed you'll be told to start a new shell.

## What this formula includes

The **full** feature set, web UI included — `why serve` works out of the box. The formula vendors all 24 transitive dependencies as Homebrew resources.

Only `pydantic-core` (via FastAPI) needs a compiler, which is why `rust` is a build dependency. whydatApp dropped `uvicorn[standard]` in 2.3.7 specifically to keep `uvloop`, `httptools`, `watchfiles`, and `websockets` out of this list.

## Contributing

This tap is generated. The formula is bumped automatically on every whydatApp release — don't hand-edit `Formula/why-cli.rb` expecting the change to survive. Fixes belong upstream in [Nostoi/whydatapp](https://github.com/Nostoi/whydatapp).

CI builds the formula from source and runs `brew test` on every push and weekly, because **nothing else validates a tap** — a broken formula would otherwise surface only when a user runs `brew install`.
