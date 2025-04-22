Absolutely! Here's your translated guide in English – keeping the structure, tone, and formatting clear and friendly:

---

# Shell_Customize  
**From Boring to Productive: Customize Your Shell**

This guide introduces two ways to make your terminal more useful and visually appealing:  
- Alias (→ [Jump to Alias](#alias))  
- Starship Prompt (→ [Jump to Starship](#starship))

If you're not sure which shell you're using:  
```bash
echo $SHELL
```

---

## Alias  
![alias](pic/alias.png)

With `alias`, you can define **shortcuts** for recurring commands. Alias is a shell builtin and works in most shells, like **bash**, **zsh**, and **fish**.

### Step-by-Step:

**1. Open your config file (depending on the shell):**
- **bash**: `vim ~/.bashrc`
- **zsh** (e.g. with Oh My Zsh): `vim ~/.zshrc`
- **fish**: `vim ~/.config/fish/config.fish`

**2. Add aliases, for example:**
```bash
alias gs='git status'
alias ..='cd ..'
alias ll='ls -lah'
alias update='sudo apt update && sudo apt upgrade'
```

**3. Reload your config:**
```bash
source ~/.zshrc    # for zsh
```

**Now you can use `ll` instead of typing `ls -lah` every time.**

---

## Starship  
![starship](pic/starship.png)

**Starship** is a fast, beautiful, and highly customizable prompt for **any shell on any system**.

### Benefits
- 🚀 **Blazingly fast**
- ⚙️ **Fully configurable**
- 🧠 **Smart – shows only relevant info**
- 🌐 **Universal – works everywhere**
- ❤️ **Easy to install**

---

### Install Starship without `sudo`

**1. Create a target directory:**
```bash
mkdir -p ~/.local/bin
```

**2. Download & extract the binary:**
```bash
curl -LO https://github.com/starship/starship/releases/latest/download/starship-x86_64-unknown-linux-musl.tar.gz
tar -xvzf starship-x86_64-unknown-linux-musl.tar.gz
mv starship ~/.local/bin/
```

**3. Add local path to your shell config:**
```bash
export PATH="$HOME/.local/bin:$PATH"
```

*(If `~/.local/bin` isn't already in your `$PATH`)*

---

### 4. Initialize Starship (depending on your shell):

```bash
# Bash
echo 'eval "$(starship init bash)"' >> ~/.bashrc

# Zsh
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

Then:
```bash
source ~/.zshrc
```

---

### 5. Test it

```bash
starship --version
```

If the version shows up, the installation worked ✅

---

### 6. Common Issue

If Starship doesn’t appear when restarting the shell, the path might be missing.  
Add this **before the `eval`** line in `.bashrc` or `.zshrc`:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

---

## 🎨 Customize Starship

### 1. Create a config file:
```bash
mkdir -p ~/.config
vim ~/.config/starship.toml
```

### 2. Example configuration

#### Define the format
```toml
format = """
$username\
$hostname\
$directory\
$git_branch\
$git_status\
$character
"""
```

#### Customize individual modules:
```toml
[username]
style = "blue"
show_always = true

[directory]
truncation_length = 5
truncate_to_repo = false
style = "cyan"
```
😎 You can find an example configuration [here](src/starship.md).  
➡️ More customization options: 📚 [Starship Docs](https://starship.rs/config/)

---

### 🎁 Bonus: Starship Presets

Starship offers pre-made layouts, like the "Pastel Powerline" preset:

```bash
starship preset pastel-powerline \
  --output ~/.config/starship.toml
```

![example](pic/exampel_pastel.png)

Find more ready-to-use layouts on the [DevOpsToolkit Starship Presets page](https://devopstoolkit.live/terminal/from-boring-to-productive-customize-your-shell-prompt-with-starship/#starship-presets).

---

✅ **Conclusion:** Alias + Starship = more clarity, efficiency, and fun in the terminal 🚀

---

Let me know if you want a downloadable version (like PDF or HTML) or want to localize it even more!