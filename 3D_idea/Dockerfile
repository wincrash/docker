FROM wincrash/docker3d
MAINTAINER ruslan pacevic

RUN apt-get update && apt-get install -y --force-yes qtcreator default-jdk qt5-default qtscript5-dev libqt5script5 libqt5scripttools5 libqt5svg5-dev libqt5webkit5-dev libqt5xmlpatterns5-dev qttools5-dev-tools qttools5-dev libxt-dev libtiff5-dev libwrap0-dev && apt-get clean
RUN wget http://download.jetbrains.com/python/pycharm-community-4.5.3.tar.gz && tar xfz pycharm-community-4.5.3.tar.gz

CMD ["/bin/bash"]

