Elixir on Alpine Linux + basic development tools
=====

Elixir is a dynamic, functional language designed for building scalable and maintainable applications.

Latest version: **1.2.1**  
Image size: **57.8 MB**  
Parent: [pmbauer/elixir](https://github.com/pmbauer/alpine-elixir)

This is based on work for `msaraiva/erlang` but includes an init system for PID 1 and DNS fixes for Alpine's lack of support for `search` in `resolv.conf`.

See [Erlang/Elixir on Alpine Linux](https://github.com/msaraiva/alpine-erlang) to learn more about creating **minimal Erlang/Elixir docker images with Alpine Linux**.

> **Notice:** If you don't need to download and compile dependencies (i.e. just using iex or similar), you can use [pmbauer/elixir](https://registry.hub.docker.com/u/pmbauer/elixir/) which is much smaller.

The following packages are pre-installed:

- erlang + dependencies
- erlang-inets
- erlang-ssl
- erlang-public-key
- erlang-crypto
- erlang-syntax-tools
- erlang-parsetools
- erlang-asn1
- erlang-sasl
- erlang-erl-interface
- erlang-dev
- erlang-eunit
- elixir
- wget
- git + dependencies
- rebar
- hex

> **Notice:** In order to keep images as compact as possible, Erlang libraries for Alpine Linux are split into many different packages. The full list of Erlang packages available can be found [here](https://pkgs.alpinelinux.org/packages?name=erlang%25&repo=all&arch=x86_64&maintainer=all).

## Usage

```
FROM pmbauer/elixir-dev

RUN apk --update add bash vim git-bash-completion && \
    rm -rf /var/cache/apk/*

RUN git clone https://github.com/elixir-lang/vim-elixir.git ~/.vim

RUN curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh -o ~/.git-prompt.sh

ADD prompt.sh /etc/profile.d/prompt.sh
ADD aliases.sh /etc/profile.d/aliases.sh
ADD gitconfig /root/.gitconfig

CMD ["/bin/bash", "-l"]
```
