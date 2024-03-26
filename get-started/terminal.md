# Terminal

## Terminal profiles

Example `settings.toml` configuration:

```toml
[terminal]
# ...

[terminal.default-profile]
macos   = "default"
linux   = "toolbox"
windows = "pwsh"

[terminal.profiles.default]

[terminal.profiles.toolbox]
commmand    = "toolbox"
arguments   = ["enter"]
workdir     = "/root"
environment = { SSH_AUTH_SOCK = "/run/user/100/ssh.sock" }

[terminal.profiles.pwsh]
command = "pwsh"
```
