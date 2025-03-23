# Ubuntu Installation

## Resources
- [Ubuntu desktop](https://ubuntu.com/desktop)
- [Balena Etcher](https://etcher.balena.io/)

## Guidelines
- Follow standard installer instructions
  - Once installed, run the following commands:
      - Update: `sudo apt update && sudo apt upgrade -y`
      - Drivers installation: `sudo ubuntu-drivers install`
      - Nala installation
          - `sudo apt install nala -y`
          - `sudo nala fetch`
          - Choose the closest repositories: 1 2 3
      - Installation of additional packages: <br> `sudo nala install git vim wget curl tmux htop tree exa mc fzf screenfetch cmatrix tasksel tldr zsh tar net-tools github-cli`
        - Updating tldr: `tldr --update`
        - Konsole profile configuration
        - Tasksel setup: `sudo tasksel` and then `reboot`
        - [Google Chrome](https://www.google.com/intl/en_ca/chrome/browser-tools/?_gl=1*s5hvhi*_up*MQ..&gclid=CjwKCAjw26KxBhBDEiwAu6KXt_e_dRbUCJ1vUH1odxXLxlWIO1XV-5hSB9Yu95_h-CX7pVosoG83VxoC9rYQAvD_BwE&gclsrc=aw.ds)
        - [Jetbrains](https://www.jetbrains.com/toolbox-app/)
        - [NordVPN](https://nordvpn.com/offer/download/linux/?vpn=brand&nc=Search_-_Canada_-_Brand_+_Generic_-_Exact+Phrase_-_EN_-_DMT_-_USD&ns=google&nm=cpc&nt=nordvpn%20linux&gad_source=1&gclid=CjwKCAjw26KxBhBDEiwAu6KXt4OJ4wDqfa1xy-fR75WhaF3dcLMx5qw-fe20BdDtouIYYgWjV6nJwhoCFPoQAvD_BwE)
        - [OhMyZsh](https://ohmyz.sh/) installation and modification to .zshrc file with the addition of:
            - tmux
              - Creating new sessions keeping the current path:
                - `vim ~/.tmux.conf`
                - `bind c new-window -c "#{pane_current_path}"`
                - `bind % split-window -h -c "#{pane_current_path}"`
                - `bind '"' split-window -v -c "#{pane_current_path}"`
                - `:wq`
                - `tmux source-file ~/.tmux.conf`
            - alias update='sudo apt update && sudo apt upgrade -y'
            - alias fzfq='vim $(fzf --preview="cat {}")'
            - alias exaq='exa --oneline --long --all --tree --level=2'
            - [powerlevel10k](https://dev.to/trevorzylks/using-powerlevel10k-to-customize-zsh-4f8o)
            - Conda
                - [Download](https://www.anaconda.com/download)
                - [Installation](https://docs.anaconda.com/free/anaconda/install/linux/)
                - Installation from ~/Downloads
                - `which -p conda`
                - Addition to .zshrc:
                ```
                # >>> conda initialize >>>
                # !! Contents within this block are managed by 'conda init' !!
                  __conda_setup="$('/home/carlos/anaconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
                if [ $? -eq 0 ]; then
                  eval "$__conda_setup"
                else
                  if [ -f "/home/carlos/anaconda3/etc/profile.d/conda.sh" ]; then
                                    . "/home/carlos/anaconda3/etc/profile.d/conda.sh"
                  else
                                    export PATH="/home/carlos/anaconda3/bin:$PATH"
                  fi
                fi
                unset __conda_setup
                # <<< conda initialize <<<
                ```