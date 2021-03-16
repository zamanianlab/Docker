FROM continuumio/miniconda3
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update && apt-get install -y procps
RUN apt-get install -y cmake gcc g++

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a

# compile hhsuite
RUN git clone https://github.com/soedinglab/hh-suite.git
RUN	mkdir hh-suite/build && cd /hh-suite/build && \
   cmake -DCMAKE_INSTALL_PREFIX=. .. && \
   make -j 4 && make install
ENV PATH="/hh-suite/build/bin:/hh-suite/build/scripts:$PATH"

# install TMHMM
RUN wget
RUN tar -xzvf
