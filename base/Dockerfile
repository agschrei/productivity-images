FROM ubuntu:20.04

WORKDIR /root

RUN apt update && apt upgrade -y && apt install zsh curl git htop build-essential ca-certificates dpkg-dev jq python3 python3-pip fonts-powerline -y --no-install-recommends
RUN chsh -s $(which zsh)
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
RUN curl -OL https://github.com/wagoodman/dive/releases/download/v0.10.0/dive_0.10.0_linux_amd64.deb && apt install ./dive_0.10.0_linux_amd64.deb -y && rm ./dive_0.10.0_linux_amd64.deb
ENV TERM "xterm-256color"
COPY *.zsh* ./
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
ENTRYPOINT [ "/bin/zsh" ]