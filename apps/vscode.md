# Visual Studio Code

## Keybindings

- paste and execute **shell command**    
  requires a terminal to exist
    ```powershell
    {
        "key": "ctrl+alt+r",
        "command": "workbench.action.terminal.sendSequence",
        "args": {
            "text": "\u0001git-publish\u000D"
        },
        "when": "terminal.active"
    },
    ```