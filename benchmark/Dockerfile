FROM wincrash/centos6
MAINTAINER Ruslan Pacevic <rpacevic@gmail.com>
RUN yum -y install iperf
COPY bonnie++-1.97.tgz /
COPY iozone3_405.tar /
COPY l_lpk_p_11.1.2.005.tgz /
COPY stream.c /
RUN cd / && tar xzf l_lpk_p_11.1.2.005.tgz &&  tar xf iozone3_405.tar && tar xfz bonnie++-1.97.tgz &&  cd /iozone3_405/src/current/ && make linux-AMD64 && cd /bonnie++-1.97.1 && ./configure && make && cd / && gcc -O2 -DSTREAM_ARRAY_SIZE=30000000 -fopenmp stream.c -o stream-bin

