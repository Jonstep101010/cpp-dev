FROM --platform=$TARGETPLATFORM mcr.microsoft.com/devcontainers/base:bookworm
# add apt sources for llvm
RUN curl -fsSL https://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add -
RUN echo "deb http://apt.llvm.org/bookworm/ llvm-toolchain-bookworm-18 main" >> /etc/apt/sources.list.d/llvm.list
RUN apt-get update --fix-missing && apt-get -y upgrade

# install dependencies
RUN apt-get install -y wget gnupg gnupg2 gdb autoconf automake autotools-dev libtool bash

# install & alias llvm tools
RUN apt-get install -y --no-install-recommends clang-18 clangd-18 clang-format-18 clang-tidy-18
RUN ln -s /usr/bin/clang-format-18 /usr/local/bin/clang-format
RUN ln -s /usr/bin/clang-tidy-18 /usr/local/bin/clang-tidy
RUN ln -s /usr/bin/clang-18 /usr/bin/clang
RUN ln -s /usr/bin/clangd-18 /usr/bin/clangd

RUN apt-get install -y libclang-rt-18-dev-dbgsym clang-tools-18 libllvm18 llvm-18 llvm-18-dev llvm-18-runtime \
		libclang-common-18-dev libclang-18-dev libclang1-18 libfuzzer-18-dev libclang-rt-18-dev
RUN ln -s /usr/bin/llvm-symbolizer-18 /usr/local/bin/llvm-symbolizer
RUN ln -s /usr/bin/scan-build-18 /usr/local/bin/scan-build
RUN ln -s /usr/bin/clang++-18 /usr/local/bin/clang++