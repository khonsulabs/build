FROM ubuntu:18.04

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
    && rm -rf /var/lib/apt/lists/*

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - \
    && apt-get install -yqq nodejs \
    && npm install -g sass \
    && npm install -g rollup \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install awscli

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

ENV PATH="/root/.cargo/bin/:${PATH}" CARGO_HOME="/root/.cargo" RUSTUP_HOME="/root/.rustup" 

RUN rustup install nightly && rustup default stable && rustup show

RUN cargo install cargo-tarpaulin \
    && cargo install wasm-pack \
    && cargo install cargo-make \
    && cargo install sccache

ENV RUSTC_WRAPPER="/root/.cargo/bin/sccache"
