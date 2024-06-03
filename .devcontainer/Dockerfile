FROM --platform=$TARGETPLATFORM mcr.microsoft.com/devcontainers/base:bookworm

# change sources to testing
RUN sed -i 's/bookworm/testing/g' /etc/apt/sources.list.d/debian.sources
RUN touch /etc/apt/sources.list.d/sources.list
RUN sed -i 's/bookworm/testing/g' /etc/apt/sources.list.d/sources.list
RUN apt-get update

RUN apt-get install -y \
	cmake valgrind gdb wget gnupg gnupg2 autoconf automake autotools-dev libtool bash

# add compiler & tools
RUN apt-get install -y \
	llvm-17-tools llvm-17-dev clang-17 libclang-rt-17-dev llvm-17-runtime libclang-17-dev \
	clangd-17 clang-format-17 clang-tidy-17 libfuzzer-17-dev

RUN apt-get -y upgrade

RUN ln -s /usr/bin/clang-format-17 /usr/local/bin/clang-format && \
	ln -s /usr/bin/clang-tidy-17 /usr/local/bin/clang-tidy && \
	ln -s /usr/bin/clang-17 /usr/bin/clang && \
	ln -s /usr/bin/clangd-17 /usr/bin/clangd && \
	ln -s /usr/bin/llvm-symbolizer-17 /usr/local/bin/llvm-symbolizer && \
	ln -s /usr/bin/scan-build-17 /usr/local/bin/scan-build && \
	ln -s /usr/bin/scan-view-17 /usr/local/bin/scan-view && \
	ln -s /usr/bin/clang++-17 /usr/local/bin/clang++