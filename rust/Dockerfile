FROM ubuntu:18.04

RUN apt-get update \
    && apt-get upgrade -yqq \
    && apt-get install -yqq \
        cmake \
        curl \
        libssl-dev \
        pkg-config \
        wget \
        zlib1g-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

RUN rustup install nightly

RUN cargo install cargo-tarpaulin
