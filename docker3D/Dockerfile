FROM ubuntu:15.04
MAINTAINER ruslan pacevic
RUN echo "deb http://ftp.de.debian.org/debian sid main" >>/etc/apt/sources.list
RUN apt-get update && apt-get install -y --force-yes mesa-utils xserver-xorg-video-all bash-completion wget nano mc htop git cmake-curses-gui g++ libXext-dev && apt-get clean
VOLUME ["/work"]
VOLUME ["/data"]
EXPOSE 22
EXPOSE 21000
EXPOSE 22000
EXPOSE 80
EXPOSE 8080
EXPOSE 8282
EXPOSE 8484

CMD ["/bin/bash"]

