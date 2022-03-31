# List of software installed in MBP

- https://superuser.com/questions/330497/why-does-os-x-not-have-a-default-package-manager
- MacOS doesn’t have inbuilt package manager.Mac OS X has MacPorts, Fink, and Homebrew, but those are all third-party package managers
- Installing Home Brew -> https://brew.sh/
  - nano ~/.zshrc
  - export PATH=/opt/homebrew/bin:$PATH
- Installing OhMyZsh -> sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
- After downloading the vscode :
  - Move ur vscode app to Application folder
  - To use code . To open any project in vscode use ->
    - nano ~/.zshrc
    - export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
- Ref: https://stackoverflow.com/questions/29955500/code-not-working-in-command-line-for-visual-studio-code-on-osx-mac
  - OhMyZsh theme -> jonathan
- brew install wget
