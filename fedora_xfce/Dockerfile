FROM fedora
MAINTAINER ruslan pacevic

# Install the appropriate software
RUN dnf -y install firefox  tigervnc-server xterm  dejavu-sans-fonts dejavu-serif-fonts xdotool tar wget nano mc htop which git gcc-c++ make cmake openmpi-devel pwgen xauth qt-creator 
RUN dnf -y groupinstall  'Xfce Desktop' 

# Add the xstartup file into the image and set the default password.
RUN mkdir /root/.vnc
ADD ./xstartup /root/.vnc/
RUN chmod -v +x /root/.vnc/xstartup
RUN echo vislt | vncpasswd -f > /root/.vnc/passwd
RUN chmod -v 600 /root/.vnc/passwd


EXPOSE 5901
EXPOSE 3389
EXPOSE 22
EXPOSE 21000
EXPOSE 22000
EXPOSE 80
EXPOSE 8080
EXPOSE 8282
EXPOSE 8484
VOLUME ["/work"]
VOLUME ["/data"]
RUN dnf install qt5-*-devel tcp_wrappers-devel qt5-qttools-static libXt-devel libtiff-devel patch mesa-libGLU-devel libXi-devel
CMD    ["vncserver", "-fg" ]
# ENTRYPOINT ["vncserver", "-fg" ]
