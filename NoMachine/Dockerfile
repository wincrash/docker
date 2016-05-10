FROM ubuntu


ENV DEBIAN_FRONTEND=noninteractive

# Helpers
RUN apt-get update
RUN apt-get install -y vim xterm

RUN apt-get install -y pulseaudio cups mate-desktop-environment-core

RUN apt-get install -y wget

RUN wget http://download.nomachine.com/download/4.6/Linux/nomachine-workstation-evaluation_4.6.12_8_amd64.deb
RUN dpkg -i nomachine-workstation-evaluation_4.6.12_8_amd64.deb

RUN groupadd -r nomachine -g 433 && \
useradd -u 431 -r -g nomachine -d /home/nomachine -s /bin/bash -c "NoMachine" nomachine && \
mkdir /home/nomachine && \
chown -R nomachine:nomachine /home/nomachine && \
echo 'nomachine:nomachine' | chpasswd

EXPOSE 4000

ADD nxserver.sh /

CMD ["/bin/sh", "/nxserver.sh"]
