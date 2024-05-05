# Visual Studio Code Hacks

1. Toggle between terminal and editor with single shortcut. Add the following to keybindings.json. You can open it from command palette, preferences Open Keyboard Shortcuts (JSON)
   
        [
            {
                "key":     "ctrl+`",
                "command": "workbench.action.terminal.focus"
            },
            {
                "key":     "ctrl+`",
                "command": "workbench.action.focusActiveEditorGroup",
                "when":    "terminalFocus"
            }
        ]

