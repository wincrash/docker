FROM wincrash/centos7
MAINTAINER Ruslan Pacevic <rpacevic@gmail.com>

RUN yum -y install freeglut-devel python-devel libXt-devel openmpi-devel mesa-libOSMesa-devel 

RUN wget http://www.vtk.org/files/release/6.2/VTK-6.2.0.tar.gz && tar xfz /VTK-6.2.0.tar.gz -C /  && mkdir /VTK-6.2.0/build && cd /VTK-6.2.0/build && a="$(nproc)" && cmake -DVTK_Group_Web:BOOL=ON -DVTK_WRAP_PYTHON:BOOL=ON -DVTK_Group_Imaging:BOOL=ON -DVTK_Group_MPI:BOOL=ON -DVTK_Group_Views:BOOL=ON .. && make  -j $a install

