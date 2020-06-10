FROM ubuntu:18.04

MAINTAINER dilmnqvovpnmlib <simplelpmis6@gmail.com>

ENV PYTHONUNBUFFERED 1

ENV TZ Asia/Tokyo

RUN apt update
RUN apt -y upgrade

RUN apt install -y git vim less
RUN apt install -y build-essential clang cmake llvm-dev lldb libncurses5-dev python3 git strace pkg-config

RUN mkdir /workspace
WORKDIR /workspace

ADD docker-entrypoint.sh /workspace

# Install apps
RUN git clone https://github.com/ytakano-lecture/tinydbg.git
RUN git clone https://github.com/ytakano-lecture/tinyregex.git

# make file
RUN cd tinydbg/ext/libelfin && make && make install
RUN echo Hello0
RUN cd /workspace

RUN cd tinydbg/src && make
RUN echo Hello1
RUN cd /workspace

RUN cd tinyregex/src && make
RUN echo Hello2
RUN cd /workspace

# Setting .bashrc
RUN { \
    echo "alias ll='ls -l'"; \
    echo "alias la='ls -A'"; \
    echo "alias l='ls -CF'"; \
    echo "PS1='\[\e[1;34m\][\u@\h \W]\\$ \[\e[m\]'"; \
    } > ~/.bashrc
