# Theme

Developing a theme plugin for Lapce is easy. Firstly [open settings](../get-started/settings.md), change colours in theme settings, then change the UI appearance in UI Settings.

<figure><img src="../.gitbook/assets/theme_settings.png" alt=""><figcaption></figcaption></figure>

[Open command palette](../get-started/command-palette.md), choose the command `Export current settings to a theme file`, it will generate the theme file for you.

<figure><img src="../.gitbook/assets/theme_export_file.png" alt=""><figcaption></figcaption></figure>

Change the name of the theme, and save the file.

To create a theme plugin for Lapce, follow the format of this repo [https://github.com/lapce/atom-one](https://github.com/lapce/atom-one), the important files are `volt.toml` and the theme file.

After that is done, you can [publish it](plugin-development.md#publish-plugin).
