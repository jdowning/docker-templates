FROM ubuntu:14.04.1
MAINTAINER Justin Downing <justin@downing.us>
ENV REFRESHED_AT 2014-08-14

# update apt and install deps
RUN apt-get update -qq
RUN apt-get install -y build-essential curl git libreadline-dev libssl-dev zlib1g-dev

# install rbenv, ruby-build
RUN git clone https://github.com/sstephenson/rbenv.git /usr/local/rbenv
RUN mkdir /usr/local/rbenv/plugins
RUN git clone https://github.com/sstephenson/ruby-build.git /usr/local/rbenv/plugins/ruby-build

# setup rbenv paths
RUN echo 'export RBENV_ROOT=/usr/local/rbenv'  >> /etc/profile.d/rbenv.sh
RUN echo 'export PATH="$RBENV_ROOT/bin:$PATH"' >> /etc/profile.d/rbenv.sh
RUN echo 'eval "$(rbenv init -)"'              >> /etc/profile.d/rbenv.sh
RUN chmod +x /etc/profile.d/rbenv.sh

# build ruby
ENV RBENV_ROOT /usr/local/rbenv
ENV PATH $RBENV_ROOT/bin:$RBENV_ROOT/shims:$PATH
ENV CONFIGURE_OPTS --disable-install-doc
RUN rbenv install 2.1.2
RUN $RBENV_ROOT/versions/2.1.2/bin/gem install bundler
RUN rbenv global 2.1.2
