FROM ubuntu:14.04
MAINTAINER Justin Downing <justin@downing.us>
ENV REFRESHED_AT 2014-11-05

# update apt and install deps
RUN apt-get update -qq
RUN apt-get install -y build-essential curl git libreadline-dev libssl-dev zlib1g-dev

# install ruby-build
RUN mkdir /src
RUN git clone https://github.com/sstephenson/ruby-build.git /src/ruby-build
RUN /src/ruby-build/install.sh
RUN rm -rf /src/ruby-build

# build ruby
ENV CONFIGURE_OPTS --disable-install-doc
RUN ruby-build 2.1.3 /usr/local
RUN gem update --system
RUN gem install bundler

# cleanup
RUN apt-get autoremove -y
RUN rm -rf /tmp/*
