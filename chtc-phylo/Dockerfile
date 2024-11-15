FROM --platform=linux/amd64 mambaorg/micromamba:jammy

# install (nf tracing)
USER 0
RUN apt update && apt install -y --no-install-recommends \
    procps cmake gcc g++ git && \
    rm -r /var/lib/apt/lists/*

# fix lockfile problems: https://stackoverflow.com/questions/76778360/micromamba-install-gets-stuck-when-run-in-docker-container-on-arm-mac
RUN micromamba config set extract_threads 1

# copy the environment.yml file to the container
COPY --chown=$MAMBA_USER:$MAMBA_USER conda_env.yml .

# install dependencies
RUN micromamba install -n base -y -f conda_env.yml && \
    micromamba clean -a -y

ARG MAMBA_DOCKERFILE_ACTIVATE=1  

# create install directory to compile and install additional programs
RUN mkdir install

#install tmhmm2
COPY /install/TH2.tar.gz .
RUN \
	mv TH2.tar.gz install && cd install \
&& tar -xzvf TH2.tar.gz && rm TH2.tar.gz

ENV PATH="tmp/install/tmhmm-2.0c/bin:$PATH"

#install signalp5
COPY /install/SP5.tar.gz .
RUN \
  mv SP5.tar.gz install && cd install \
&& tar -xzvf SP5.tar.gz && rm SP5.tar.gz

ENV PATH="tmp/install/signalp-5.0b/bin:$PATH"

#install hmmtop
COPY /install/HT21.tar.gz .
RUN \
  mv HT21.tar.gz install && cd install \
&& tar -xzvf HT21.tar.gz && rm HT21.tar.gz \
&& cd hmmtop_2.1 && cc hmmtop.c -lm -o hmmtop \
&& cd .. && cd ..

ENV PATH="tmp/install/hmmtop_2.1:$PATH"