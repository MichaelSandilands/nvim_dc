# Neovim Data Science Dev Container

A fully configured development environment for Python Data Science, built on
**Miniconda** and **Neovim**.

This setup is optimized for the
**[Kitty Terminal](https://sw.kovidgoyal.net/kitty/)** to enable inline image
rendering with **[Molten.nvim](https://github.com/benlubas/molten-nvim)** and
**[image.nvim](https://github.com/3rd/image.nvim)**.

## Features

* 🐍 **Miniconda** base with Python 3.10
* ⚡ **Neovim** (latest stable) installed via Homebrew
* 📊 **Data Science Stack**: Pandas, Numpy, Scikit-learn, PyTorch (ready), and
more via `environment.yml`
* 🖼️ **Graphics Support**: Pre-configured SSH server to forward Kitty graphics
protocol (required for plots in terminal)
* 📝 **Quarto & Jupyter**: Support for `.ipynb` and `.qmd` files

## Prerequisites

* [Docker](https://www.docker.com/)
* [Dev Containers CLI](https://github.com/devcontainers/cli) (or VS Code with
the Dev Containers extension)
* [Kitty Terminal](https://sw.kovidgoyal.net/kitty/) (Required for viewing plots)

---

## 🚀 Quick Start

### 1. Build the Container

Initialize and build the dev container. This will install all tools defined in
`devcontainer.json` and set up the conda environment.

```bash
devcontainer up --workspace-folder . --remove-existing-container
```

### 2. Set Up SSH Credentials

The container runs an SSH server (listening on localhost:2222) to allow Kitty to
communicate properly. You need to set a password for the `vscode` user once
after building.

Enter the container's shell:

```bash
devcontainer exec --workspace-folder . bash
```

Set a password (e.g., `vscode` or your choice):

```bash
sudo passwd $(whoami)
```

> You can exit the shell (`exit`) after setting the password.

### 3. Connect via Kitty SSH

To see images and plots inside Neovim, you **must** connect using the
`kitten ssh` wrapper. This forwards the necessary graphics sockets.

```bash
kitten ssh -p 2222 vscode@localhost
```

Once connected, navigate to your workspace:

```bash
cd /workspaces/nvim_dc/
```

## Usage Tips

### Connecting to a Persistent Kernel

If you need to debug kernel issues or want to connect to a kernel that persists
after you close Neovim, you can start it manually in the terminal:

```bash
jupyter kernel --kernel=python3
```
