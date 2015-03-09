
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
RUN /bin/bash -l -c "gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3"
RUN /bin/bash -l -c "curl -L https://get.rvm.io | bash -s stable"
RUN /bin/bash -l -c "rvm requirements"
ENV RUBY_VERSION 2.2.0
RUN /bin/bash -l -c "rvm install $RUBY_VERSION"

# Install bundler
RUN /bin/bash -l -c "gem install bundler --no-ri --no-rdoc"

