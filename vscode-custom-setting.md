## Make ZSH as default integrated terminal in vscode rather than /bin/bash

- https://askubuntu.com/questions/1117868/change-default-terminal-back-to-bash-in-vs-code
- settings
- search for : terminal.integrated.shell.linux
- Edit in setting.json
-   "terminal.integrated.shell.linux": "/usr/bin/zsh",  (Replace this key value pair to /usr/bin/zsh rather than /bin/bash)
