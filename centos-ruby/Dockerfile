FROM centos:7
MAINTAINER Sergey Nesterov <qnesterr@gmail.com>
RUN yum -y install epel-release \
  make \
  gcc \
  git \
  openssl-devel \
  zlib-devel \
  mysql-devel \
  redis \
  sqlite-devel \
  openssl-devel \
  readline-devel\
  zlib-devel \
  wget \
  curl \
  dtach \
  vim \
  hash-slinger \
  bzip2 \
  tar \
  ImageMagick \
  ImageMagick-devel \
  libffi-devel \
  mysql-devel \
  libxslt-devel \
  python \
  postgresql-devel \
  which \
  ruby-build

RUN yum clean all

# Install and setup rbenv
ENV RBENV_ROOT /usr/local/rbenv
RUN git clone https://github.com/sstephenson/rbenv.git $RBENV_ROOT
RUN git clone https://github.com/sstephenson/ruby-build.git $RBENV_ROOT/plugins/ruby-build
RUN $RBENV_ROOT/plugins/ruby-build/install.sh
ENV PATH $RBENV_ROOT/bin:$RBENV_ROOT/shims:$PATH
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
RUN chmod +x /etc/profile.d/rbenv.sh
RUN ./etc/profile.d/rbenv.sh
RUN rm /usr/local/bin/rbenv-install

# Install ruby
RUN rbenv install 2.7.1
RUN rbenv global 2.7.1 && rbenv rehash
RUN curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash

RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
RUN gem install --force --no-document bundler:2.1.4
