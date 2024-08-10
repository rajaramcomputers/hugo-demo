---
title: "Setting Alias in WSL"
draft: false
categories:
  - WSL
tags:
  - alias
---
## For Bash:
1. **Open the `.bashrc` file** in your home directory using a text editor:

    ```bash
    nano ~/.bashrc
    ```

2. **Add the following line** at the end of the file:

    ```bash
    alias k=kubectl
    ```

3. **Save the file and exit** the editor:

    - Press `Ctrl + O` to save.
    - Press `Enter` to confirm.
    - Press `Ctrl + X` to exit.

4. **Apply the changes** by sourcing the `.bashrc` file:

    ```bash
    source ~/.bashrc
    ```

## For Zsh:

1. **Open the `.zshrc` file** in your home directory using a text editor:

    ```bash
    nano ~/.zshrc
    ```

2. **Add the following line** at the end of the file:

    ```bash
    alias k=kubectl
    ```

3. **Save the file and exit** the editor:

    - Press `Ctrl + O` to save.
    - Press `Enter` to confirm.
    - Press `Ctrl + X` to exit.

4. **Apply the changes** by sourcing the `.zshrc` file:

    ```bash
    source ~/.zshrc
    ```

---

After following these steps, the alias `k=kubectl` will be permanent in your WSL environment, allowing you to use `k` as a shortcut for `kubectl` in future sessions.
