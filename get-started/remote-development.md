# Remote Development

Lapce has a remote development feature, which you can connect Lapce to a remote machine via SSH. After connecting to the remote machine, all the plugins, and commands will be run from the remote machine. You would have exactly the same experience as if you were working a local workspace, without feeling any differences.

To use it, click the blue remote icon on the top left

<figure><img src="../.gitbook/assets/remote_ssh_button.png" alt=""><figcaption></figcaption></figure>

It will pop up the input box for you to put in the SSH connection details. You can use the hostname you configured in your `~/.ssh/config`

<figure><img src="../.gitbook/assets/remote_ssh_palette.png" alt=""><figcaption></figcaption></figure>

Upon successful ssh connection, lapce will attempt to download proxy directly from remote host, and in case of failure, it will try to download it through your local host and upload it to remote machine. Once `lapce-proxy` downloaded and started on the remote machine your local Lapce instance establishes a connection to it via SSH tunnel.  

After it's connected, it will show a green connected status on the remote development icon. Then you can start to `Open folder` as if you are opening a local folder.

<figure><img src="../.gitbook/assets/remote_ssh_connected.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/remote_ssh_workspace_opened.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Remote development only works with key based SSH authentication at the moment. So it doesn't connect if you normally put a password for connecting to the SSH host.
{% endhint %}
