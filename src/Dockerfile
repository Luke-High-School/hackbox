FROM ubuntu:20.04
USER luke

ENV HOME /home/luke
WORKDIR $HOME


######### Customize Container Here ###########

RUN sudo apt update
RUN sudo apt -y upgrade
RUN sudo apt -y install openvpn
RUN sudo apt -y install unzip

# Change Background to sth cool
COPY assets/mr-robot-wallpaper.png  /usr/share/extra/backgrounds/bg_default.png

# Install Starship
RUN wget https://starship.rs/install.sh
RUN sudo chmod +x install.sh
RUN sudo ./install.sh -y

# Add Starship to bashrc
RUN echo 'eval "$(starship init bash)"' >> .bashrc

# Add Starship Theme
COPY config/starship.toml .config/starship.toml

# Install Hack Nerd Font
RUN wget https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Hack.zip
RUN sudo unzip Hack.zip -d /usr/local/share/fonts

# Install Terminator
RUN sudo apt -y install terminator

# Set up Nerd font in Terminator
RUN sudo mkdir .config/terminator
COPY config/terminator.toml .config/terminator/config

# Install XFCE Dark Theme
RUN sudo apt install numix-gtk-theme


######### End Customizations ###########

RUN sudo chown 1000:0 $HOME

ENV HOME /home/luke
WORKDIR $HOME
RUN sudo mkdir -p $HOME && chown -R 1000:0 $HOME
