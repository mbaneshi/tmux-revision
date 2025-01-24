## Timestamp: 2025-01-25  
### Description: Enabling clipboard yank/paste functionality in Neovim for TTY  
### Lines: 29  
### Characters: 1855  
```bash
nvim enable_clipboard_tty.md
```

To enable clipboard functionality in Neovim for a TTY-only Ubuntu server, you’ll need a tool that acts as a clipboard manager compatible with terminal environments. Since you have **brew** and **internet**, follow these steps:

---

### 1. **Install `xclip` or `xsel`**
These are commonly used tools to manage clipboard data on headless systems. Since you're using `brew`, install `xclip`:

```bash
brew install xclip
```

Alternatively, install `xsel` if you prefer:

```bash
brew install xsel
```

---

### 2. **Configure Neovim Clipboard Provider**
LazyVim uses **`nvim`'s default clipboard integration**. To enable this functionality:

1. Open your `init.lua` or the LazyVim config directory:
   ```bash
   nvim ~/.config/nvim/init.lua
   ```
   or if LazyVim overrides:
   ```bash
   nvim ~/.config/nvim/lua/config/options.lua
   ```

2. Ensure the following is set to enable clipboard support:
   ```lua
   vim.o.clipboard = "unnamedplus"
   ```

---

### 3. **Set Clipboard Commands**
For TTY, you need to bind the Neovim clipboard provider to `xclip` or `xsel`. Add this to your Neovim configuration (e.g., in `~/.config/nvim/init.lua`):

```lua
if vim.fn.has("clipboard") == 0 then
  vim.g.clipboard = {
    name = "xclip",
    copy = {
      ["+"] = "xclip -selection clipboard",
      ["*"] = "xclip -selection primary",
    },
    paste = {
      ["+"] = "xclip -selection clipboard -o",
      ["*"] = "xclip -selection primary -o",
    },
  }
end
```

---

### 4. **Reload Neovim Configuration**
Reload your Neovim configuration or restart Neovim:
```bash
:source ~/.config/nvim/init.lua
```

---

### 5. **Test the Clipboard**
1. Yank some text in Neovim:
   ```bash
   " +y  (Yanks to system clipboard)
   ```
2. Outside of Neovim, try pasting in TTY:
   ```bash
   Shift + Insert
   ```

---

### Troubleshooting:
- If you face any issues:
  - Ensure `xclip` or `xsel` is correctly installed and accessible in your `$PATH`.
  - Check the Neovim log with:
    ```bash
    :checkhealth
    ```

This setup enables you to yank in Neovim and paste directly into the TTY!
