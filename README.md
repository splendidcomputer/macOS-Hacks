# macOS-Hacks
Here we share the tricks we use for macOS.


You want to run `code` (VS Code) from the terminal, but you’re seeing this error:

> `EACCES: permission denied, unlink '/usr/local/bin/code'`

This happens because the VS Code installer is trying to create or update the symlink `/usr/local/bin/code`, but **you don't have the necessary permissions** for that folder.

---

**Here's how to fix it:**

1. Open your **Terminal**.
2. Run this command to manually set up the symlink (with admin permissions):

```bash
sudo ln -sf "/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code" /usr/local/bin/code
```

- `sudo` gives you the required permission.
- `-s` means "create a symlink".
- `-f` forces it, overwriting if necessary.

You'll be asked for your Mac password (nothing will appear when typing — just type it and press Enter).

---

**After that**, you should be able to just type `code .` in any folder to open it in VS Code.

---

**Small tip:**  
If you prefer, you can also set up this from inside VS Code:
- Open **VS Code**.
- Press `Cmd+Shift+P`.
- Type `Shell Command: Install 'code' command in PATH` and select it.

If it still fails, you definitely need to fix it manually with `sudo` as shown above.
