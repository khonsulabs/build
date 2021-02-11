FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get upgrade -yqq \
    && apt-get install -yqq \
        cmake \
        curl \
        libssl-dev \
        pkg-config \
        python3-pip \
        wget \
        zlib1g-dev \
        uuid-runtime \
        openssh-client \
        libclang-dev \
        xorg \
        xorg-dev \
        git-core \
        zip \
        libxcb-render-util0-dev \
        libxcb-shape0-dev \
        libxcb-xfixes0-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - \
    && apt-get install -yqq nodejs \
    && npm install -g sass \
    && npm install -g rollup \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install awscli

RUN wget https://github.com/WebAssembly/binaryen/archive/version_99.tar.gz && \
    mkdir /root/binaryen && \
    tar -xzf version_99.tar.gz -C /root/binaryen --strip-components 1 && \
    cd /root/binaryen && cmake . && make

RUN curl https://sh.rustup.rs -sSf | sh -s -- --profile minimal -y

ENV PATH="/root/.cargo/bin/:/root/binaryen/bin:${PATH}" CARGO_HOME="/root/.cargo" RUSTUP_HOME="/root/.rustup" 

RUN rustup install nightly && rustup default stable && rustup show

RUN cargo install grcov \
    && cargo install wasm-bindgen-cli \
    && cargo install cargo-make 
