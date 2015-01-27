#######################
# Github Jekyll pages #
# #####################
#
# Build image:
# sudo docker build -t username/github-pages .
# Start container:
# (map host port 4000 to container port 4000)
# (github-pages on container is current directory on host)
# sudo docker run --rm -p 4000:4000 -v $(pwd):/github-pages -it username/github-pages
#
# Use debian wheezy as base image
FROM debian:wheezy

# Install ruby
RUN apt-get update \
    && apt-get install -y \
    build-essential zlib1g-dev ruby ruby-dev ruby1.9.1-dev \
    node \
    python-pygments

# Install bundler
RUN gem install bundler

# Install github-pages
WORKDIR /tmp
RUN printf "source 'https://rubygems.org'\ngem 'github-pages'" > Gemfile
RUN bundle install

# Mount point for host is the working directory /github-pages, container listens to port 4000
RUN mkdir /github-pages
WORKDIR /github-pages
VOLUME /github-pages
EXPOSE 4000

# Always use that command on docker run
ENTRYPOINT exec bundle exec jekyll serve
