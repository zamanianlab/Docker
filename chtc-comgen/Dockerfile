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

#install tmhmm2
COPY /install/TH2.tar.gz .
RUN \
	mv TH2.tar.gz install && cd install \
&& tar -xzvf TH2.tar.gz && rm TH2.tar.gz

ENV PATH="/install/tmhmm-2.0c/bin:$PATH"

#install signalp5
COPY /install/SP5.tar.gz .
RUN \
  mv SP5.tar.gz install && cd install \
&& tar -xzvf SP5.tar.gz && rm SP5.tar.gz

ENV PATH="/install/signalp-5.0b/bin:$PATH"

#install hmmtop
COPY /install/HT21.tar.gz .
RUN \
  mv HT21.tar.gz install && cd install \
&& tar -xzvf HT21.tar.gz && rm HT21.tar.gz \
&& cd hmmtop_2.1 && cc hmmtop.c -lm -o hmmtop

ENV PATH="/install/hmmtop_2.1:$PATH"
