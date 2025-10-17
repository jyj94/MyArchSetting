# regreet 설치
<pre><code>pacman -S greetd-regreet</code></pre>

# 기본 설정

```/etc/greetd/config.toml```
```
[default_session]
command = "Hyprland --config /path/to/custom/hyprland/config"
user = "greeter"
```

```/etc/greetd/hyprland.conf```
```
exec-once = regreet; hyprctl dispatch exit
misc {
	disable_hyprland_logo = true
	disable_splash_rendering = true
	disable_hyprland_qtutils_check = true
}
```
```/etc/greetd/regreet.toml```
<pre><code>
# SPDX-FileCopyrightText: 2022 Harish Rajagopal <harish.rajagopals@gmail.com>
#
# SPDX-License-Identifier: GPL-3.0-or-later

[background]
# Path to the background image
path = "/usr/share/backgrounds/greeter.jpg"

# How the background image covers the screen if the aspect ratio doesn't match
# Available values: "Fill", "Contain", "Cover", "ScaleDown"
# Refer to: https://docs.gtk.org/gtk4/enum.ContentFit.html
# NOTE: This is ignored if ReGreet isn't compiled with GTK v4.8 support.
fit = "Contain"

# The entries defined in this section will be passed to the session as environment variables when it is started
[env]
ENV_VARIABLE = "value"

[GTK]
# Whether to use the dark theme
application_prefer_dark_theme = true

# Cursor theme name
cursor_theme_name = "Adwaita"

# Whether to blink the cursor
cursor_blink = true

# Font name and size
font_name = "Cantarell 16"

# Icon theme name
icon_theme_name = "Adwaita"

# GTK theme name
theme_name = "Adwaita"

[commands]
# The command used to reboot the system
reboot = ["systemctl", "reboot"]

# The command used to shut down the system
poweroff = ["systemctl", "poweroff"]

# The command prefix for X11 sessions to start the X server
x11_prefix = [ "startx", "/usr/bin/env" ]

[appearance]
# The message that initially displays on startup
greeting_msg = "Welcome back!"


[widget.clock]
# strftime format argument
# See https://docs.rs/jiff/0.1.14/jiff/fmt/strtime/index.html#conversion-specifications
format = "%a %H:%M"

# How often to update the text
resolution = "500ms"

# Override system timezone (IANA Time Zone Database name, aka /etc/zoneinfo path)
# Remove to use the system time zone.
timezone = "America/Chicago"

# Ask GTK to make the label at least this wide. This helps keeps the parent element layout and width consistent.
# Experiment with different widths, the interpretation of this value is entirely up to GTK.
label_width = 150
</code></pre>

# systemd 등록
systemd에 등록하여 부팅 시 자동으로 시작하도록 만듬
```
sudo sytemctl enable greetd
```
