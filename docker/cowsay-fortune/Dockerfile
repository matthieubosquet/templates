#########################################
# Cow says fortunes beautiful container #
#########################################
#
# Build image:
# sudo docker build -t username/cowsay-fortune .
# Start container (--rm to remove it on exit):
# sudo docker run --rm username/cowsay-fortune
#
# Use debian wheezy as base image
FROM debian:wheezy

# Install cowsay, fortune and fortune files (-y to say yes during install)
RUN apt-get update && apt-get install -y cowsay fortune fortunes-debian-hints fortunes-off

# Add /usr/games to the $PATH environment variable
# n.b.
# We could specify the full command path and not modify $PATH:
# ENTRYPOINT exec /usr/games/fortune | /usr/games/cowsay
ENV PATH $PATH:/usr/games

# Set command run by the container (exec to stop it nicely)
ENTRYPOINT exec fortune | cowsay
