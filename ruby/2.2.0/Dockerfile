
FROM debian

MAINTAINER Lefteris Laskaridis <lefteris.laskaridis@gmail.com>

RUN groupadd -r ruby && useradd -r -g ruby -d /home/ruby -m ruby && chsh -s /bin/bash ruby

RUN apt-get update && apt-get install -y \
	build-essential \
	curl \
	git \
	zlib1g-dev \
	libssl-dev \
	libreadline-dev \
	libyaml-dev \
	libxml2-dev \
	libxslt-dev \
	gawk \ 
	libsqlite3-dev \
	sqlite3 \
	autoconf \
	libgdbm-dev \
	libncurses5-dev \
	automake \
	libtool \
	bison \
	pkg-config \
	libffi-dev \
	openssl \
	libtool \
	procps

# Switch to non-root user
USER ruby
WORKDIR /home/ruby

# Install rvm and ruby
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -L https://get.rvm.io | bash -s stable
ENV PATH /home/ruby/.rvm/bin:$PATH
RUN rvm requirements
RUN rvm install 2.2.0 --default
ENV PATH /home/ruby/.rvm/rubies/ruby-2.2.0/bin:$PATH

# Install bundler
RUN gem install bundler --no-ri --no-rdoc

