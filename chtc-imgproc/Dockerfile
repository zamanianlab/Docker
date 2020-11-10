FROM continuumio/miniconda3
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update && apt-get install -y procps

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a
