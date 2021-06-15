FROM ubuntu:20.04

WORKDIR /root

# make sure we have a 256 color terminal available so we can configure p10k with a fancy prompt
ENV TERM "xterm-256color"
ENV DEBIAN_FRONTEND=noninteractive
#opencontainers labels
LABEL org.opencontainers.image.authors="Alexander Gschrei"
LABEL org.opencontainers.image.url="https://github.com/agschrei/productivity-images"
LABEL org.opencontainers.image.documentation="https://github.com/agschrei/productivity-images/blob/main/README.md"
LABEL org.opencontainers.image.source="https://github.com/agschrei/productivity-images.git"
LABEL org.opencontainers.image.licenses="MIT"

RUN apt update && apt upgrade -y && apt install zsh curl git htop build-essential tmux vim ca-certificates dpkg-dev jq python3 python3-pip fonts-powerline -y --no-install-recommends

ARG username=debug

# add non-root user and set zsh as default shell
RUN useradd -m ${username} -s $(which zsh)

WORKDIR /home/${username}

USER ${username}:0

# install oh-my-zsh
RUN ZSH=/home/${username}/.oh-my-zsh; sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
COPY --chown=${username}:0 *.zsh* ./

ENTRYPOINT [ "/bin/zsh" ]