FROM ubuntu:18.04

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
        snapd \
    && rm -rf /var/lib/apt/lists/*

RUN snap install node --classic --channel=12 && npm install -g sass

RUN pip3 install awscli

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

ENV PATH="/root/.cargo/bin/:${PATH}" CARGO_HOME="/root/.cargo" RUSTUP_HOME="/root/.rustup" 

RUN rustup install nightly && rustup default stable && rustup show

RUN cargo install cargo-tarpaulin && cargo install cargo-web
