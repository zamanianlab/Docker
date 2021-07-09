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

# update nextflow
RUN nextflow self-update

# install guppy
RUN wget -O guppy-4.5.2.tar.gz "https://mirror.oxfordnanoportal.com/software/analysis/ont-guppy-cpu_4.5.2_linux64.tar.gz"
RUN tar -xzvf guppy-4.5.2.tar.gz
ENV PATH=/ont-guppy-cpu/bin:$PATH
