FROM continuumio/miniconda3:4.9.2
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update
RUN apt-get install -y 'procps' \
    'ffmpeg'\
    'libsm6'\
    'libxext6'  -y

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a

RUN export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
RUN export PATH=$PATH:/home/ubuntu/.local/bin
