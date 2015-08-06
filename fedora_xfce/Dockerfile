FROM fedora

RUN dnf -y groupinstall \
    'Xfce Desktop' \
    && dnf clean all

# http://sigkillit.com/2013/02/26/how-to-remotely-access-linux-from-windows/
COPY Xclients /etc/skel/.Xclients

RUN dnf -y install \
    scap-security-guide \
    scap-workbench \
    supervisor \
    xrdp \
    && dnf clean all

RUN useradd ruslan && echo ruslan:vislt | chpasswd && echo root:vislt | chpasswd

# Configure supervisord to run session manager and xrdp.
COPY xrdp.ini /etc/supervisord.d/

# Allow all users to connect via RDP.
RUN sed -i '/TerminalServerUsers/d' /etc/xrdp/sesman.ini && \
    sed -i '/TerminalServerAdmins/d' /etc/xrdp/sesman.ini

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

CMD ["supervisord", "-n"]

RUN dnf -y install tar wget nano mc htop which git gcc-c++ make cmake openmpi-devel pwgen xauth qt-creator 
