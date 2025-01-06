# Use the official micromamba base image
FROM mambaorg/micromamba:jammy

# install mysql server and java
USER 0
RUN apt update && apt install -y --no-install-recommends \
    make gcc build-essential libgtk-3-dev wget git vim \
    mysql-server libmysqlclient-dev \
    openjdk-11-jdk-headless && \
    rm -r /var/lib/apt/lists/*

# copy the environment.yml file to the container
COPY --chown=$MAMBA_USER:$MAMBA_USER conda_env.yml /tmp/env.yml

# fix lockfile problems: https://stackoverflow.com/questions/76778360/micromamba-install-gets-stuck-when-run-in-docker-container-on-arm-mac
RUN micromamba config set extract_threads 1

# install dependencies
RUN micromamba install -y -n base -f /tmp/env.yml && \
    micromamba clean --all --yes

ARG MAMBA_DOCKERFILE_ACTIVATE=1  

# clone wrmxpress
ARG CACHEBUST=1
RUN echo ${CACHEBUST} && git clone --branch v2.0 https://github.com/zamanianlab/wrmXpress.git

# The code to run when container is started:
ENTRYPOINT ["/usr/local/bin/_entrypoint.sh"]
