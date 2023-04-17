# single-user-nix

A set of scripts intended for use on RHEL 7 to create a reliable single user
rootless installation of nix.

Non-functional: this is basically a broken down, more readable version of the
``--no-daemon`` nix installation script, with the /nix directory being
bindmounted with ``unshare`` instead of using root to mount on the host system.
However, at time of writing this suffers from the same issues as the no-daemon
installation on RHEL-7, namely:

```txt
error: changing ownership of path '/nix/store': Invalid argument
```

This error could probably be solved if I had more in-depth knowledge of what
exactly unshare does, and also maybe if I read the code that goes into the
``nix-store`` binary. However, [nix-portable](https://github.com/DavHau/nix-portable)
exists, which does exactly what I intended to do here.
