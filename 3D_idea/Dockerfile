FROM wincrash/docker3d
MAINTAINER ruslan pacevic

RUN apt-get update && apt-get install -y --force-yes qtcreator default-jdk && apt-get clean
RUN wget http://download.jetbrains.com/python/pycharm-community-4.5.3.tar.gz && tar xfz pycharm-community-4.5.3.tar.gz

CMD ["/bin/bash"]

