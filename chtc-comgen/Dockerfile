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

# create install directory to compile and install additional programs
RUN mkdir install

# install hhsuite
RUN \
	cd install && git clone https://github.com/soedinglab/hh-suite.git \
&& mkdir hh-suite/build && cd /install/hh-suite/build \
&& cmake -DCMAKE_INSTALL_PREFIX=. .. \
&& make -j 4 && make install

ENV PATH="/install/hh-suite/build/bin:/install/hh-suite/build/scripts:$PATH"

#install hmmtop
COPY /install/TH2.tar.gz .
RUN \
	mv TH2.tar.gz install && cd install \
&& tar -xzvf TH2.tar.gz \