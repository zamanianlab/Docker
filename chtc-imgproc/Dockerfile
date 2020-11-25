FROM continuumio/miniconda3
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update
RUN apt-get install -y 'procps' \
    'ffmpeg'\
    'libsm6'\
    'libxext6'  -y

#install dev version of scikit-image
git clone https://github.com/scikit-image/scikit-image.git
cd scikit-image
pip install -e .

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a
