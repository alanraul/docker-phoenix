FROM alpine:3.16
LABEL maintainer="Alan Raúl <raulumb@gmail.com>"
ARG DEBIAN_FRONTEND=noninteractive

ENV ERLANG_VERSION=23.3.4.4
ENV ELIXIR_VERSION=1.12.3-otp-23
ENV PHOENIX_VERSION=1.6.14
ENV NODE_VERSION=14.20.1

RUN \
    apk add --no-cache --update \
      grep \
      bash \
      ca-certificates \
      openssl-dev \
      ncurses-dev \
      libressl-dev \
      unixodbc-dev \
      zlib-dev curl gcc \
      make automake \
      autoconf gnupg yarn \
      inotify-tools
RUN \
    apk add --no-cache \
      dpkg-dev \
      dpkg \
      binutils \
      git \
      autoconf \
      build-base \
      perl-dev
  RUN apk --no-cache add -U musl musl-dev ncurses-libs libssl1.1 libressl3.5-libcrypto bash \
      qt5-qtwebengine qt5-qtbase-x11 qt5-qtsvg qt5-qtdeclarative qt5-qtsvg qt5-qtbase
  RUN apk add --update-cache \
      xvfb \
      dbus \
      ttf-freefont \
      fontconfig weasyprint

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN touch ~/.bashrc
RUN git clone https://github.com/asdf-vm/asdf.git ~/.asdf
ENV KERL_CONFIGURE_OPTIONS --disable-silent-rules --without-javac --enable-shared-zlib --enable-dynamic-ssl-lib --enable-hipe --enable-sctp --enable-smp-support --enable-threads --enable-kernel-poll --enable-wx --disable-debug --without-javac --enable-darwin-64bit
ENV PATH /root/.asdf/bin:/root/.asdf/shims:${PATH}

RUN /bin/bash -c "source ~/.bashrc"

## Erlang
RUN /bin/bash -c "asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git"
RUN /bin/bash -c "asdf install erlang $ERLANG_VERSION"
RUN /bin/bash -c "asdf global erlang $ERLANG_VERSION"

## Elixir
RUN /bin/bash -c "asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git"
RUN /bin/bash -c "asdf install elixir $ELIXIR_VERSION"
RUN /bin/bash -c "asdf global elixir $ELIXIR_VERSION"
RUN /bin/bash -c "rm -rf ~/.asdf/installs/elixir/ref-$ELIXIR_COMMIT/lib/mix/tmp/"

## Nodejs
RUN /bin/bash -c "asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git"
RUN /bin/bash -c "asdf install nodejs $NODE_VERSION"
RUN /bin/bash -c "asdf global nodejs $NODE_VERSION"

## Phoenix
RUN /bin/bash -c "mix local.hex --force"
RUN /bin/bash -c "mix local.rebar --force"
RUN /bin/bash -c "mix archive.install --force hex phx_new $PHOENIX_VERSION"