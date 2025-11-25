# Custom CLI Utilities

A collection of useful command-line utilities and shell functions for daily development work.

## Installation

### 1. Clone or Copy Scripts to ~/.local/bin

If cloning this repository:
```bash
git clone <repository-url> ~/.local/bin
```

Or if you already have files in ~/.local/bin, you can clone to a temporary location and copy:
```bash
git clone <repository-url> /tmp/custom-bin
cp /tmp/custom-bin/* ~/.local/bin/
```

### 2. Make Scripts Executable

```bash
chmod +x ~/.local/bin/*
```

### 3. Add ~/.local/bin to Your PATH

Add the following line to your shell configuration file:

**For Zsh** (~/.zshrc):
```bash
export PATH="$HOME/.local/bin:$PATH"
```

**For Bash** (~/.bashrc or ~/.bash_profile):
```bash
export PATH="$HOME/.local/bin:$PATH"
```

Then reload your shell configuration:
```bash
source ~/.zshrc  # for zsh
# or
source ~/.bashrc  # for bash
```

### 4. Set Up Shell Aliases/Functions

The `aliases` file contains useful shell functions. To use them:

**For Zsh:**

Option A: Add to your main config (~/.zshrc):
```bash
source ~/.local/bin/aliases
```

Option B: If you have a dedicated aliases directory (e.g., ~/.zsh/):
```bash
mkdir -p ~/.zsh
cp ~/.local/bin/aliases ~/.zsh/aliases.zsh
```

Then add to ~/.zshrc:
```bash
source ~/.zsh/aliases.zsh
```

Option C: If using Oh My Zsh:
```bash
mkdir -p ~/.oh-my-zsh/custom
cp ~/.local/bin/aliases ~/.oh-my-zsh/custom/aliases.zsh
```
Oh My Zsh will automatically load files from the custom directory.

**For Bash** (~/.bashrc):
```bash
source ~/.local/bin/aliases
```

After adding, reload your shell:
```bash
source ~/.zshrc  # or source ~/.bashrc
```

## Available Scripts

- **copy** - Cross-platform clipboard copy utility (supports pbcopy, xclip, putclip)
- **cpwd** - Copy current working directory to clipboard
- **hoy** - Date/time utility
- **jsonformat** - Format JSON output
- **line** - Line manipulation utility
- **mkcd** - Create directory and cd into it (also available as function)
- **murder** - Kill processes by name
- **pasta** - Cross-platform clipboard paste utility (supports pbpaste, xclip)
- **pastas** - Plural version of pasta
- **prettypath** - Display PATH in a readable format
- **rn** - Rename utility
- **running** - Show running processes
- **timer** - Set a timer with notification
- **trash** - Move files to trash instead of deleting
- **url** - URL manipulation utility
- **uuid** - Generate UUIDs
- **waitfor** - Wait for a condition

## Available Aliases/Functions

- **mkcd** - Create a directory and immediately cd into it
  ```bash
  mkcd new-project
  ```

- **tempe** - Create and cd into a temporary directory with secure permissions
  ```bash
  tempe          # Creates temp dir
  tempe mydir    # Creates temp dir with subdirectory
  ```

- **boop** - Play a sound based on the last command's exit status (requires sfx command)
  ```bash
  some-command && boop  # Plays "good" sound on success, "bad" on failure
  ```

## Verification

To verify everything is set up correctly:

1. Check that scripts are in your PATH:
   ```bash
   which copy
   # Should output: /home/rich/.local/bin/copy
   ```

2. Check that functions are loaded:
   ```bash
   type mkcd
   # Should output: mkcd is a shell function
   ```

3. Test a script:
   ```bash
   echo "test" | copy
   pasta
   # Should output: test
   ```

## Dependencies

Some scripts may require additional tools:
- **copy/pasta**: Works best with `xclip` on Linux or `pbcopy/pbpaste` on macOS
- **timer**: Requires `sfx` and `notify` commands
- **boop**: Requires `sfx` command

Install xclip on Ubuntu/Debian:
```bash
sudo apt install xclip
```

## Troubleshooting

**Scripts not found after adding to PATH:**
- Make sure you reloaded your shell configuration (`source ~/.zshrc`)
- Verify PATH contains ~/.local/bin: `echo $PATH | grep .local/bin`
- Check that scripts are executable: `ls -la ~/.local/bin/copy`

**Functions not working:**
- Ensure you sourced the aliases file in your shell config
- Reload your shell: `exec zsh` or `exec bash`
- Check if function is loaded: `type mkcd`
