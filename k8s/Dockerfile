FROM agschrei/productivity-images:base
# install kubectl and verify the binary  
ARG TARGETARCH
ARG HELM_VERSION=3.6.0
# the expected mount location for kubectl config
ENV KUBECONFIG k8s/config
RUN printenv
RUN echo "Installing kubectl binary for ${TARGETARCH}" &&\
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/${TARGETARCH}/kubectl" &&\
    curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/${TARGETARCH}/kubectl.sha256" &&\
    echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check &&\
    rm kubectl.sha256 &&\
    chmod +x ./kubectl &&\
    mkdir -p ~/.local/bin/ &&\
    mv ./kubectl ~/.local/bin/
RUN echo "Installing helm binary for ${TARGETARCH}" && \
    curl -LO https://get.helm.sh/helm-v${HELM_VERSION}-linux-${TARGETARCH}.tar.gz &&\
    curl -LO https://get.helm.sh/helm-v${HELM_VERSION}-linux-${TARGETARCH}.tar.gz.sha256sum &&\
    cat helm-v${HELM_VERSION}-linux-${TARGETARCH}.tar.gz.sha256sum | shasum --check &&\
    tar -zxvf helm-v${HELM_VERSION}-linux-${TARGETARCH}.tar.gz &&\
    mv linux-${TARGETARCH}/helm ~/.local/bin/ && rm -rf helm-* linux-*
RUN echo "PATH=~/.local/bin/:$PATH" >> .zshrc