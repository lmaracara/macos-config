# 💤 LazyVim

A starter template for [LazyVim](https://github.com/LazyVim/LazyVim).
Refer to the [documentation](https://lazyvim.github.io/installation) to get started.

## Prerequisites

Before setting up this LazyVim configuration, make sure you have Neovim installed. You can install it by applying the Homebrew configuration from this repository.

See the [Homebrew README](../homebrew/README.md) for instructions on how to install packages from the Brewfile, which includes Neovim along with other development tools.

## How to Apply

To use this LazyVim configuration, you need to link this `nvim` folder to the location where Neovim expects its configuration on macOS.

1. First, make sure the `~/.config` directory exists:
   ```bash
   mkdir -p ~/.config
   ```

2. From the repository root, create a symbolic link from this `nvim` folder to `~/.config/nvim`:
   ```bash
   ln -s $(pwd)/nvim ~/.config/nvim
   ```
   
   Or using an absolute path (replace with your actual repository path):
   ```bash
   ln -s /path/to/macos-config/nvim ~/.config/nvim
   ```

3. If you already have a `~/.config/nvim` directory, you may want to back it up first:
   ```bash
   mv ~/.config/nvim ~/.config/nvim.backup
   ```

4. After linking, launch Neovim and LazyVim will automatically set up the plugins and configuration.
