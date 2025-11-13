# Terminal Configuration with .zshrc

This guide helps you set up your terminal using the provided `.zshrc` for a modern, productive shell experience on macOS.

## Prerequisites

Before using this configuration, install:

### 1. Homebrew
A package manager for macOS.  
[Homebrew Installation Guide](https://brew.sh/)

**Install Homebrew:**
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

For Apple Silicon Macs, you may need to add Homebrew to your PATH:
```sh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### 2. iTerm2
A powerful terminal emulator for macOS.  
**Recommended:** Install via Homebrew:
```sh
brew install --cask iterm2
```

Alternatively, [Download iTerm2](https://iterm2.com/) manually.

**Note:** `Brewfile` in the `homebrew/` directory already include iterm2. See the [Homebrew README](../homebrew/README.md) for installation details.

### 3. Oh My Zsh
A popular framework for managing your Zsh configuration.  
[Oh My Zsh Installation Guide](https://ohmyz.sh/#install)

### 4. Powerlevel10k Theme
A fast, flexible, and beautiful Zsh prompt.  
[Powerlevel10k GitHub](https://github.com/romkatv/powerlevel10k)

**Install Powerlevel10k:**
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```
**NOTE** After linking this zshrc and sourcing it the p10k configuration wizzard will automatically appear.

## Plugin Installation

This configuration uses several plugins. Many of the required tools can be installed via Homebrew, which is the recommended approach.

**Recommended:** Install packages via Homebrew using the `Brewfile`:
```sh
cd /path/to/macos-config/homebrew
brew bundle install --file=Brewfile
```

This will install all required packages including `fzf`, `bat`, and `thefuck`. See the [Homebrew README](../homebrew/README.md) for more details.

**Manual Installation (if needed):**

- **fzf** ([GitHub](https://github.com/junegunn/fzf))
	```sh
	brew install fzf
	$(brew --prefix)/opt/fzf/install
	```
	**Note:** After installing via Homebrew, update the `Brewfile` in the `homebrew/` directory. See the [Homebrew README](../homebrew/README.md) for details.

- **bat** ([GitHub](https://github.com/sharkdp/bat))
	```sh
	brew install bat
	```
	**Note:** Required for the `zsh-bat` plugin. After installing via Homebrew, update the `Brewfile` in the `homebrew/` directory.

- **thefuck** ([GitHub](https://github.com/nvbn/thefuck))
	```sh
	brew install thefuck
	```
	**Note:** After installing via Homebrew, update the `Brewfile` in the `homebrew/` directory.

- **zsh-autosuggestions** ([GitHub](https://github.com/zsh-users/zsh-autosuggestions))
	```sh
	git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
	```

- **zsh-syntax-highlighting** ([GitHub](https://github.com/zsh-users/zsh-syntax-highlighting))
	```sh
	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
	```

- **you-should-use** ([GitHub](https://github.com/MichaelAquilina/zsh-you-should-use))
	```sh
	git clone https://github.com/MichaelAquilina/zsh-you-should-use $ZSH_CUSTOM/plugins/you-should-use
	```

- **zsh-bat** ([GitHub](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zsh-bat))
	```sh
	git clone https://github.com/fdellwing/zsh-bat.git $ZSH_CUSTOM/plugins/zsh-bat
	```
	**Note:** Requires `bat` to be installed (see above).

## How to Use This .zshrc

1. **Backup your current .zshrc (optional):**
	 ```sh
	 mv ~/.zshrc ~/.zshrc.backup
	 ```
2. **Link the provided .zshrc:**
	 ```sh
	 ln -s $(pwd)/.zshrc ~/.zshrc
	 ```
3. **Reload your shell:**
	 ```sh
	 source ~/.zshrc
	 ```

## Additional Notes

- Customize aliases and user settings in the `.zshrc` as needed.
- For prompt customization, edit `~/.p10k.zsh` or run `p10k configure`.
- **Important:** If you install any new packages via Homebrew (e.g., `brew install <package>`), remember to update the `Brewfile` in the `homebrew/` directory. See the [Homebrew README](../homebrew/README.md) for instructions on how to bump your Brewfile.

## Extra configurations

**Configure Powerlevel10k:**  
Set the theme in your `.zshrc`:
```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```
To customize your prompt, run:
```sh
p10k configure
```

---
Enjoy your enhanced terminal experience!
