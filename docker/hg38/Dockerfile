############################################################
# Dockerfile to build DNAscan pipeline
############################################################


FROM ubuntu:latest
LABEL maintainer="Heather Marriott" email="heather.marriott@kcl.ac.uk"
SHELL ["/bin/bash", "-c"]
RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y bash
RUN cd $PWD
RUN git clone https://github.com/hevmarriott/DNAscanv2.git
RUN cd /
RUN bash DNAscanv2/scripts/install_dependencies_hg38.sh $PWD/DNAscanv2/local/ $PWD/DNAscanv2/ 
RUN source ~/.bashrc

RUN mkdir -p /.singularity.d/env
RUN cp /DNAscanv2/docker/91-environment.sh /.singularity.d/env/91-environment.sh

WORKDIR /DNAscanv2/

ENTRYPOINT cat $PWD/DNAscanv2/docker/welcome_message.txt
