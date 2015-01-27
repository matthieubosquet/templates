##############################################
# WarMUX turn based artillery game container #
##############################################
#
# Build:
# sudo docker build -t username/warmux .
# Start:
# sudo docker run --rm username/warmux
#
# Use debian wheezy as base image
FROM debian:wheezy

# Install wormux
RUN apt-get update && apt-get install -y wormux

# Install ssh and configure it
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config
EXPOSE 22

# Run sshd to forward X11
CMD ["/usr/sbin/sshd", "-D"]
