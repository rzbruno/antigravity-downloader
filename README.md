# Antigravity Downloader & Updater

A robust Bash downloader and auto-updater for Google Antigravity on Linux (x86_64).

It manages downloads and installation for:
- **Antigravity 2.0** (Desktop Hub)
- **Antigravity IDE**
- **Antigravity CLI** (`agy`)

## Features

- **Idempotent & Smart Updates**: Checks local versions against upstream release manifests and only downloads when a newer version is released.
- **Resilient Downloads**: Uses `curl` with retries, resume support (`-C -`), and connection error handling.
- **Desktop Integration**: Automatically creates and updates `.desktop` launcher shortcuts in `~/.local/share/applications` and desktop database cache.
- **Portable**: Can be executed from any working directory or invoked via `$PATH`. Automatically ensures user binaries and symlinks in `~/.local/bin`.

## Installation & Setup

Clone the repository:

```bash
git clone https://github.com/<your-username>/antigravity-downloader.git ~/code/antigravity-downloader
```

Make the script executable (if not already):

```bash
chmod +x ~/code/antigravity-downloader/antigravity-downloader
```

Symlink to your local bin directory (ensure `~/.local/bin` is in your `$PATH`):

```bash
ln -sfn ~/code/antigravity-downloader/antigravity-downloader ~/.local/bin/antigravity-downloader
```

*(Note: The script also automatically creates and maintains this symlink upon execution).*

## Usage

Run the downloader / updater:

```bash
antigravity-downloader
```

### Options

| Flag | Description |
|------|-------------|
| `-f`, `--force` | Force download and reinstallation of all components even if already up to date |
| `-h`, `--help`  | Display help message |

## Directory Structure

Components are installed according to the XDG Base Directory specification:

- **Binaries / Symlinks**: `~/.local/bin/` (`antigravity`, `antigravity-ide`, `agy`, `antigravity-downloader`, `update-antigravity`)
- **Applications**: `~/.local/share/antigravity` and `~/.local/share/antigravity-ide`
- **Desktop Launchers**: `~/.local/share/applications/antigravity.desktop` and `antigravity-ide.desktop`
