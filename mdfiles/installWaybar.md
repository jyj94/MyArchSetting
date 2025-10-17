# waybar 설치
```sudo pacman -S waybar```

# 설정 파일 위치
```~/.config/waybar/config.jsonc``` 설정 파일
```~/.config/waybar/sytle.css``` css 설정 파일


# 기본 아이콘을 위한 폰트 설치
https://www.nerdfonts.com/font-downloads
위에서 심볼 폰트인 Symbols Nerd Font 다운로드 후 ```/usr/share/fonts/Symbol/``` 폰트에 저장

# config.jsonc

```
// -*- mode: jsonc -*-
{
    // "layer": "top", // Waybar at top layer
    // "position": "bottom", // Waybar position (top|bottom|left|right)
    "height": 38, // Waybar height (to be removed for auto height)
    // "width": 1280, // Waybar width
    "spacing": 15, // Gaps between modules (4px)
    // Choose the order of the modules
    "modules-left": [
        "hyprland/workspaces"
    ],
    "modules-center": [
        "hyprland/window"
    ],
    "modules-right": [
        "pulseaudio",
        "cpu",
        "memory",
        "network",
        "clock",
        "custom/power"
    ],
    // Modules configuration
    "hyprland/workspaces": {
        "format": "{windows}",
        "format-window-separator": "",
        "workspace-taskbar": {
            "enable": true,
            "update-active-window": true,
            "format": "{icon}",
            "icon-size": 20
        }
    },

    "hyprland/window": {
        "format": "{}"
    },

    "pulseaudio": {
        // "scroll-step": 1, // %, can be a float
        "format": "{volume}% {icon} {format_source}",
        "format-bluetooth": "{volume}% {icon} {format_source}",
        "format-bluetooth-muted": " {icon} {format_source}",
        "format-muted": " {format_source}",
        "format-source": "{volume}% ",
        "format-source-muted": "",
        "format-icons": {
            "headphone": "",
            "hands-free": "󰏳",
            "headset": "",
            "phone": "",
            "portable": "",
            "car": "",
            "default": ["", "", ""]
        },
        "on-click": "pavucontrol"
    },

    "cpu": {
        "format": " {usage}%",
        "tooltip": false
    },

    "memory": {
        "format": " {}%"
    },

    "network": {
        // "interface": "wlp2*", // (Optional) To force the use of this interface
        "format-wifi": " {essid} ({signalStrength}%)",
        "format-ethernet": "{ipaddr}/{cidr}",
        "tooltip-format": "󱡠 {ifname} via {gwaddr}",
        "format-linked": "󱞐 {ifname} (No IP)",
        "format-disconnected": "⚠ Disconnected",
        "format-alt": "{ifname}: {ipaddr}/{cidr}"
    },

    "clock": {
        // "timezone": "America/New_York",
        "tooltip-format": "<big>{:%Y %B}</big>\n<tt><small>{calendar}</small></tt>",
        "format": "{:%Y-%m-%d %H:%M}"
    },
   
    "custom/power": {
        "format" : " ",
		"tooltip": false,
		"menu": "on-click",
		"menu-file": "$HOME/.config/waybar/power_menu.xml", // Menu file in resources folder
		"menu-actions": {
			"shutdown": "shutdown",
			"reboot": "reboot",
			"suspend": "systemctl suspend",
			"hibernate": "systemctl hibernate"
		}
    }
}
```

# style.css

```
* {
	font-family: "Noto Sans Mono", "Symbols Nerd Font", sans-serif;
}
window#waybar {
	background: rgba(34, 34, 34, 0.774);
	color: #ffffff;
	font-size: 15px;
}

#custom-power {
	font-size: 20px; 
}

#workspaces {
	margin: 0px;
}
#workspaces {
	margin: 2px 0px 2px 0px;
}
#workspaces button {
	padding: 0px;
	margin: 4px;
	background: #3f2400;
}
#workspaces button.active {
	background: #fc9612;
}
```
