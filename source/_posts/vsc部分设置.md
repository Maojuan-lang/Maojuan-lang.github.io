---
title: vsc部分设置
date: 2024-10-01
---

```bash
    // terminal encoding
	"terminal.integrated.defaultProfile.windows": "Command Prompt",
    "terminal.integrated.profiles.windows": {
        "PowerShell": {
            "source": "PowerShell",
            "icon": "terminal-powershell"
        },
        "Command Prompt": {
            "path": [
                "${env:windir}\\Sysnative\\cmd.exe",
                "${env:windir}\\System32\\cmd.exe"
            ],
            "args": ["/K","chcp 65001"],
            "icon": "terminal-cmd"
        },
        "Git Bash": {
            "source": "Git Bash"
        }
    },
    // file encoding
    "files.autoGuessEncoding": true,
    // gopls server
    "go.useLanguageServer": true
```

