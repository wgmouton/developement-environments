FROM wgmouton/dev-env:base

RUN \
  wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb &&\
  dpkg -i erlang-solutions_1.0_all.deb &&\
  apt update &&\
  apt install -y esl-erlang elixir