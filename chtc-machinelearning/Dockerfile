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

RUN R -e "devtools::install_github('zamanianlab/ZamanianLabVSTools')"
RUN R -e "devtools::install_github('tidymodels/finetune')"

RUN export PATH=$PATH:/home/ubuntu/.local/bin
