# Remote Development

{% hint style="warning" %}
Currently opening workspaces via `Open folder` is not possible due to recent UI rewrite. To open a workspace when connected remotely you can use built-in terminal to run `lapce <PATH>`.
{% endhint %}

{% hint style="warning" %}
Remote development works only with a SSH key authentication. If you want to use password, you can run Lapce via terminal with option `--wait` for it to attach to stdin/stdout.
Lapce uses your host `ssh` program to handle any interaction, Lapce itself does not read `ssh` configuration, keys or any other related files.
{% endhint %}

Lapce has a remote development feature, which you can connect Lapce to a remote machine via SSH. After connecting to the remote machine, all the plugins, and commands will be run from the remote machine. You would have exactly the same experience as if you were working a local workspace, without feeling any differences.

To use it, click the remote icon on the top left

<figure><img src="../.gitbook/assets/remote_ssh_button.png" alt=""><figcaption></figcaption></figure>

It will pop up the input box for you to put in the SSH connection details. You can use `<user>@<host>` or the `Host` name (do not confuse with `HostName` in SSH) you configured in your `~/.ssh/config`.

{% hint style="warning" %}
Lapce will use your host OpenSSH installation (`ssh` program) to connect to remote target, it doesn't read that file directly so it will not display any host configuration from that file.
Palette input in Lapce will show you only recent SSH connections that you made in Lapce itself.
{% endhint %}

<figure><img src="../.gitbook/assets/remote_ssh_palette.png" alt=""><figcaption></figcaption></figure>

Upon successful ssh connection, lapce will attempt to download proxy directly from remote host, and in case of failure, it will try to download it through your local host and upload it to remote machine. Once `lapce-proxy` downloaded and started on the remote machine your local Lapce instance establishes a connection to it via SSH tunnel.  

After it's connected, it will show a green connected status on the remote development icon. Then you can start to `Open folder` as if you are opening a local folder.

<figure><img src="../.gitbook/assets/remote_ssh_connected.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/remote_ssh_workspace_opened.png" alt=""><figcaption></figcaption></figure>
