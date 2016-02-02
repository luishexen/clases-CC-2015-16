# Cloud Computing 

FROM    ubuntu:latest
MAINTAINER Alberto Castillo Lamas <alcasla90@gmail.com> Version: 1.0

# Package installing
RUN apt-get -y install wget
RUN wget -qO- https://deb.nodesource.com/setup_4.x | sudo bash -
RUN sudo apt-get install -y git nodejs
RUN node -v
RUN git clone https://github.com/alcasla/ProyectoCloudComputing.git /home/ProyectoCloudComputing
RUN cd /home/ProyectoCloudComputing && npm install