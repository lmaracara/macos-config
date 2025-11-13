# Homebrew Configuration Management

This guide helps you manage your Homebrew packages using a `Brewfile` for easy setup and migration on macOS.

## What is a Brewfile?

A `Brewfile` is a text file that lists all your Homebrew packages, casks, and taps. It allows you to:
- Export your current Homebrew setup
- Quickly install all packages on a new macOS machine
- Version control your package dependencies
- Share your setup with others

## Prerequisites

Before using this configuration, ensure you have:

### Homebrew Installed
If you don't have Homebrew installed, run:
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

For Apple Silicon Macs, you may need to add Homebrew to your PATH:
```sh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

## Bumping (Exporting) Your Homebrew Configuration

To create or update your `Brewfile` with your current Homebrew packages:

1. **Navigate to the homebrew directory:**
   ```sh
   cd /path/to/macos-config/homebrew
   ```

2. **Export your current Homebrew setup:**
   ```sh
   brew bundle dump --force --file=Brewfile
   ```
   
   This command will:
   - Create a `Brewfile` if it doesn't exist
   - Overwrite the existing `Brewfile` with your current packages
   - Include all installed packages, casks, and taps

3. **Review the generated Brewfile:**
   ```sh
   cat Brewfile
   ```

4. **Commit the changes:**
   ```sh
   git add Brewfile
   git commit -m "Update Brewfile with current packages"
   ```

### Manual Brewfile Management

You can also manually edit the `Brewfile` to:
- Remove packages you no longer need
- Add comments for organization
- Group related packages together

Example `Brewfile` structure:
```
tap "homebrew/cask"
tap "homebrew/cask-fonts"

brew "git"
brew "node"
brew "python@3.11"

cask "iterm2"
cask "visual-studio-code"
cask "google-chrome"
```

## Applying Homebrew Configuration on a New macOS Setup

To install all packages from the `Brewfile` on a new macOS machine:

1. **Clone or navigate to this repository:**
   ```sh
   cd /path/to/macos-config/homebrew
   ```

2. **Install all packages from the Brewfile:**
   ```sh
   brew bundle install --file=Brewfile
   ```
   
   This will:
   - Install all taps listed in the Brewfile
   - Install all Homebrew packages (formulae)
   - Install all macOS applications (casks)
   - **Skip packages that are already installed** - Homebrew Bundle checks your system and will not reinstall packages that are already present, making it safe to run on systems with existing installations

3. **Verify installation:**
   ```sh
   brew bundle check --file=Brewfile
   ```
   
   This command checks if all packages in the Brewfile are installed and up to date.

## Useful Commands

### Check what's missing
```sh
brew bundle check --file=Brewfile
```
This command shows which packages from the Brewfile are missing or need updates.

### Install packages (safe to run multiple times)
```sh
brew bundle install --file=Brewfile
```
**Note:** This command is idempotent - it's safe to run multiple times. It will only install packages that are missing and skip those already installed.

### Clean up packages not in Brewfile
```sh
brew bundle cleanup --file=Brewfile
```
**Note:** This will uninstall packages not listed in your Brewfile. Use with caution!

### List all installed packages
```sh
brew list
brew list --cask
```

### Update all packages
```sh
brew update
brew upgrade
```

## Best Practices

1. **Regular Updates:** Periodically bump your `Brewfile` to keep it in sync with your installed packages:
   ```sh
   brew bundle dump --force --file=Brewfile
   ```

2. **Review Before Committing:** Always review the `Brewfile` before committing to avoid including temporary or unwanted packages.

3. **Organize Your Brewfile:** Group related packages together and add comments for better organization:
   ```
   # Development Tools
   brew "git"
   brew "node"
   
   # Terminal Tools
   brew "fzf"
   brew "bat"
   ```

4. **Test on Clean System:** Before applying to a new machine, test the `Brewfile` in a clean environment if possible.

## Troubleshooting

### Package installation fails
- Check if the package name is correct: `brew search <package-name>`
- Ensure you have the correct tap: `brew tap <tap-name>`
- Update Homebrew: `brew update`

### Cask installation issues
- Some casks may require manual intervention or additional setup
- Check the cask's documentation for specific requirements

### Permission errors
- Ensure you have administrator privileges
- Some casks may require password for installation

## Additional Resources

- [Homebrew Documentation](https://docs.brew.sh/)
- [Homebrew Bundle Documentation](https://docs.brew.sh/Manpage#bundle-subcommand)
- [Homebrew Cask](https://github.com/Homebrew/homebrew-cask)

---

Enjoy your automated macOS package management!

