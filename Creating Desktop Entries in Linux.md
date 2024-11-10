tags: #linux

Desktop entries for applications, or `.desktop` files, are generally a combination of meta information resources and a shortcut of an application. These files usually reside in `/usr/share/applications/` or `/usr/local/share/applications/` for applications installed system-wide, or `~/.local/share/applications/` for user-specific applications. User entries take precedence over system entries.

Bare bones example:

```
[Desktop Entry]
Type=Application
Name=Personal File
Exec=gedit /home/user/file
Icon=gedit
```

To reload desktop entries database, run:

```bash
update-desktop-database ~/.local/share/applications
```