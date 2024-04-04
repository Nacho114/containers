# Notes

Inspired from [boxkit](https://github.com/ublue-os/boxkit/blob/main/README.md)

## Setup 

1. Before installing lazy nvim, make sure to setup git 
    - Make sure to 
    - `rm ~/.local/share/nvim/lazy`
    - `rm ~/.local/state/nvim/lazy`

The issue is that lazy tries to pull the lazy.nvim repo, but
can't since git is not properly setup in a clean install.

2. Setup pgp key, and update the key in the `.gitconfig`

3. Make fish open on login

- Note csch was not working to add the default shell, even though it should be supported! 
It was adding the shell to the root user if I look at `/etc/passwd`

Add the following to .bashrc

```bash
# Only trigger if:
# - 'fish' is not the parent process of this shell
# - We did not call: bash -c '...'
# - The fish binary exists and is executable
if [[ $(ps --no-header --pid=$PPID --format=comm) != "fish" && -z ${BASH_EXECUTION_STRING} && -x "/bin/fish" ]]; then
  shopt -q login_shell && LOGIN_OPTION='--login' || LOGIN_OPTION=''
  exec fish $LOGIN_OPTION
fi
```

## FAQ

If the `ln` is causing issues, you can just run it inside the container since 
it only needs to be run once.

```fish
ln -fs /usr/local/bin/distrobox-host-exec /usr/bin/podman
```
