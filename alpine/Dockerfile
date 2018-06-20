FROM codigobicentenario/elixir
LABEL maintainer="raulumb@gmail.com"

RUN apk --no-cache add -U nodejs nodejs-npm inotify-tools libsass libsass-dev sassc \
    && mix archive.install https://github.com/phoenixframework/archives/raw/master/phx_new.ez --force

VOLUME /app/src/deps
VOLUME /app/src/_build
