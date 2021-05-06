FROM ubuntu:xenial

# Require to install rbenv
RUN apt-get update && \
    apt-get install -y \
    git \
    build-essential \
    libssl-dev \
    libreadline-dev \
    zlib1g-dev \
    curl \
    openjdk-8-jdk \
    tzdata

# Install rbenv
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv && \
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
# Set rbenv path
ENV PATH /root/.rbenv/shims:/root/.rbenv/bin:$PATH

# Install ruby-build & ruby
RUN git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build && \
    ~/.rbenv/bin/rbenv install 3.0.0 && \
    ~/.rbenv/bin/rbenv global 3.0.0
RUN ~/.rbenv/bin/rbenv rehash

# Initiarize ruby encording
ENV RUBYOPT -EUTF-8

# Install bundler via rbenv
RUN ~/.rbenv/bin/rbenv exec gem install bundler -v 2.2.14
RUN ~/.rbenv/bin/rbenv rehash

# Install embulk
RUN curl --create-dirs -o ${HOME}/.embulk/bin/embulk -L "https://github.com/embulk/embulk/releases/download/v0.9.23/embulk-0.9.23.jar"
RUN chmod +x ${HOME}/.embulk/bin/embulk
# Set embulk path
ENV PATH /root/.embulk/bin:$PATH
