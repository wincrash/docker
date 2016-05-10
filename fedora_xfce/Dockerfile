FROM fedora
MAINTAINER ruslan pacevic
RUN dnf -y install http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-22.noarch.rpm 
RUN dnf -y install http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-22.noarch.rpm 
RUN dnf -y install tar wget nano mc htop which git gcc-c++ make cmake qt-creator glx-utils vtk-devel vtk-python vtk-qt vtk-qt-python java-1.8.0-openjdk qt5-*-devel tcp_wrappers-devel qt5-qttools-static libXt-devel libtiff-devel patch mesa-libGLU-devel libXi-devel firefox  tigervnc-server xterm freeglut-devel
RUN dnf -y groupinstall  'Xfce Desktop' 

VOLUME ["/work"]
VOLUME ["/data"]

# Add the xstartup file into the image and set the default password.
RUN mkdir /root/.vnc
ADD ./xstartup /root/.vnc/
RUN chmod -v +x /root/.vnc/xstartup
RUN echo vislt | vncpasswd -f > /root/.vnc/passwd
RUN chmod -v 600 /root/.vnc/passwd

CMD    ["vncserver", "-fg" ]
# ENTRYPOINT ["vncserver", "-fg" ]
