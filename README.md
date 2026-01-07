# nvim_dc

## Build Container

```{bash}
devcontainer up --workspace-folder . --remove-existing-container
```

## Setup Password

```{bash}
devcontainer exec --workspace-folder . bash
```

```{bash}
sudo passwd $(whoami)
```

## Enter Container via SSH

```{bash}
kitten ssh -p 2222 vscode@localhost
```

```{bash}
cd /workspaces/dir_name/
```
