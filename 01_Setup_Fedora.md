# 1.0 - VSCode

    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

    sudo dnf install code

# 2.0 - Terminal

    sudo dnf install tilix

# 2.1 - OhMyZSH

    sudo dnf instal zsh
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 2.2 - Install Fonts (for powerlevel10k)

    # See https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k
    mkdir -p ~/.local/share/fonts/
    cp ~/WORKDIR/setup_workstation/fonts/* ~/.local/share/fonts/ 
    fc-cache -fv

    # Configure VScode

    F1 -> settings.json -> User:
    
        "terminal.integrated.fontFamily": "MesloLGS NF"

    Restart VScode

    # Configure Tilix

    Einstellungen -> Profile -> Standard -> Custom Font -> Meslo Regular


# 2.3 - Install powerlevel10k

    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    sed -i 's#^ZSH_THEME=.*#ZSH_THEME="powerlevel10k/powerlevel10k"#' ~/.zshrc

# 2.4 - Set ZSH as login shell for user

    sudo usermod --shell /usr/bin/zsh $(id -un)
    source ~/.zshrc

# 2.5 - Setup powerlevel10k

    p10k configure # Generates ~/.p10k.zsh

