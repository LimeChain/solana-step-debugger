# Solana Debugger Extension

> **Note:** This is a wrapper for the locally installed tools `agave-ledger-tool` and `solana-lldb`.

## Prerequisites

### macOS

#### You need to have installed

- `agave-ledger-tool` -> `cargo install agave-ledger-tool`
- `solana-cli` -> `sh -c "$(curl -sSfL https://release.anza.xyz/stable/install)"`

#### Path for solana CLI

```sh
export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"
```

#### Optional

`anchor avm` -> `cargo install --git https://github.com/coral-xyz/anchor avm --force`

## Installation

1. Install the extension from the VS Code Marketplace.
2. Ensure you have the `Prerequisites` installed locally.

## Usage

1. Open your Solana project in VS Code.
2. Use the command palette (`Ctrl+Shift+P` or `Cmd+Shift+P`) to run `Run Agave Ledger Tool` or `Run Solana LLDB`.

### Running Agave Ledger Tool

1. Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`).
2. Select `Run Agave Ledger Tool`.
3. Enter a valid subcommand when prompted, for example:

```sh
   validate --path /path/to/ledger
```

The output will be displayed in the integrated terminal.

### Debugging a Solana Program

1. Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`).
2. Select `Run Solana LLDB`.
3. The extension will build and start debugging your Solana program using solana-lldb.

## Troubleshooting

### macOS

if you have troubles with the extension, check if you have the following things installed:

- `protobuf` -> `brew install protobuf`
- `llvm` -> `brew install llvm`

#### PATH for llvm

```sh
export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
```

### `args-dumper` Not Found Error

In `.zshrc`:

```sh
export LLDB_DEBUGSERVER_PATH="/Applications/Xcode.app/Contents/SharedFrameworks/LLDB.framework/Versions/A/Resources/debugserver"
```

### Attach Failed (Not Allowed to Attach to Process)

Look in the console messages (Console.app), near the debugserver entries, when the attach failed. The subsystem that denied the attach permission will likely have logged an informative message about why it was denied.

Go to:

- `System Preferences` -> `Privacy & Security` -> `Developer Tools` -> `Grant access to Terminal`

On some machines, the step below could also fix the issue:

### Permission Denied When Trying to Debug a Program

Refer to this [Apple Developer Forum thread](https://forums.developer.apple.com/forums/thread/17452) to disable debugging protection for macOS systems.
