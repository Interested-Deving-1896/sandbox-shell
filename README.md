[update-readmes]   Mode: rewrite — migrating to template structure...
# sandbox-shell

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/sandbox-shell)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/sandbox-shell.git
cd sandbox-shell
```

## Usage


```
sx [OPTIONS] [PROFILES]... [-- <COMMAND>...]
```

```bash
# Offline (default)
sx -- npm run build
sx -- ./scripts/setup.sh

# Localhost only - for dev servers
sx localhost -- npm start

# Online
sx online rust -- cargo audit
sx bun online -- bun install

# Debug what's blocked
sx --trace -- cargo build       # Real-time violation log
sx --explain rust               # Show allowed/denied
sx --dry-run rust               # Preview seatbelt profile
```

### Options

| Option | Description |
|--------|-------------|
| `-v, --verbose` | Show sandbox configuration |
| `-d, --debug` | Log all denials |
| `-t, --trace` | Real-time violation stream |
| `--trace-file <PATH>` | Write trace to file |
| `-n, --dry-run` | Print profile, don't execute |
| `-c, --config <PATH>` | Use specific config |
| `--no-config` | Ignore all configs |
| `--explain` | Show what's allowed/denied |
| `--init` | Create `.sandbox.toml` |
| `--offline` | Block network (default) |
| `--online` | Allow network |
| `--localhost` | 127.0.0.1 only |
| `--allow-read <PATH>` | Allow read |
| `--allow-write <PATH>` | Allow write |
| `--deny-read <PATH>` | Deny read (overrides allows) |

| `--trace` shows violations from *all* sandboxed processes on the system, not just yours. macOS limitation.

## Configuration


### Global Config (`~/.config/sx/config.toml`)

Your personal paths go here. Terminal, shell prompt, directory jumper…

```toml
[filesystem]
allow_read = [
    # Shell prompt
    "~/.config/starship.toml",
    "~/.cache/starship/",

    # zoxide
    "~/.local/share/zoxide/",

    # Ghostty users - you need this or terminal breaks in sandbox
    "/Applications/Ghostty.app/Contents/Resources/terminfo",

    # Claude Code plugins
    # "~/projects/my-plugins/",
]

allow_write = [
    "~/.local/share/zoxide/",
    "~/Library/Application Support/zoxide/",
    "~/.cache/",
]
```

**Ghostty users:** add that terminfo path or you'll get display issues.

### Project Config (`.sandbox.toml`)

Per-project overrides:

```bash
sx --init
```

```toml
[sandbox]
profiles = ["rust"]

[filesystem]
allow_write = ["/tmp/build"]

[shell]
pass_env = ["NODE_ENV", "DEBUG"]
```

Custom profiles go in `~/.config/sx/profiles/name.toml`. They support filesystem paths, env vars, exec sugid, and raw seatbelt rules for advanced sandbox operations. See [docs/PROFILES.md](docs/PROFILES.md).

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/sandbox-shell`](https://github.com/Interested-Deving-1896/sandbox-shell) and mirrored through:

```
Interested-Deving-1896/sandbox-shell  ──►  OpenOS-Project-OSP/sandbox-shell  ──►  OpenOS-Project-Ecosystem-OOC/sandbox-shell
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[MIT](https://github.com/Interested-Deving-1896/sandbox-shell/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
