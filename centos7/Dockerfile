FROM centos:centos7
MAINTAINER Ruslan Pacevic <rpacevic@gmail.com>

RUN yum -y install openssh-server epel-release && \
    yum -y install pwgen && \    
    rm -f /etc/ssh/ssh_host_dsa_key /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && \
    sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && \
    sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config

COPY set_root_pw.sh /set_root_pw.sh
COPY run.sh /

EXPOSE 22
EXPOSE 21000
EXPOSE 22000
EXPOSE 80
EXPOSE 8080
EXPOSE 8282
EXPOSE 8484

RUN chmod +x /*.sh && useradd vislt && echo "vislt:vislt" | chpasswd 
ENV AUTHORIZED_KEYS **None**
ENV AUTHORIZED_KEYS1 ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDg+4eeCm36F9XWHHPLF1EHdm2Zt2VLNSjeyYccRenbPNAUJ7wRnhME+8LH8RQUHiyeyzjDyEOV1x7AWrdXhSF6UAeeakAD8dq89KL2WFJqfv+lM3OfifGdW1Bfe20s4diemlOwyb/IgOE3QPdib0Q0jA1DDu2MyWtrIvdYfhUIbKf+3tMDyNipLW54OEzRm4awzwBMlUPqQPeJoIR2P1gcX+NsQasSrSJykqBKPdmHFpicCfzoEzfbjxfmZLE6WLNLy6ewhO/aCEA6brbQDq/13fGRfOA06R/29hVyXItNwP3gX9aLC8cfETa1E/vOfOZoOfJPlM5XjsngPDUHcJkd ruslan@sc-ruslan.vgtu.lt

RUN mkdir -p /root/.ssh && echo $AUTHORIZED_KEYS1 >>/root/.ssh/authorized_keys && chmod 600 /root/.ssh/authorized_keys
RUN mkdir -p /home/vislt/.ssh && echo $AUTHORIZED_KEYS1 >>/home/vislt/.ssh/authorized_keys && chown -R vislt:vislt /home/vislt && chmod 600 /home/vislt/.ssh/authorized_keys

RUN yum -y install rpm-build yum-utils tar wget nano mc htop which git gcc-c++ make cmake openmpi-devel
ENV PATH=/usr/lib64/openmpi/bin:$PATH
ENV LD_LIBRARY_PATH=/usr/local/lib:/usr/lib64/openmpi/lib:$LD_LIBRARY_PATH
RUN echo "PATH=/usr/lib64/openmpi/bin:$PATH" >> /etc/profile.d/myenv.sh && echo "LD_LIBRARY_PATH=/usr/local/lib:/usr/lib64/openmpi/lib:$LD_LIBRARY_PATH" >> /etc/profile.d/myenv.sh

CMD ["/run.sh"]
