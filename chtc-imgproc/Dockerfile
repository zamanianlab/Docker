FROM continuumio/miniconda3
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

# install dev version of scikit-image
RUN pip install -i https://pypi.anaconda.org/scipy-wheels-nightly/simple scikit-image
