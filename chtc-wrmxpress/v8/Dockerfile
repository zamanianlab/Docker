FROM continuumio/miniconda3:25.1.1-2

RUN apt-get update && apt-get install -y \
    procps libsm6 libxext6\
    default-libmysqlclient-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# install conda packages
COPY conda_env.yml .
RUN \
    conda env update -n base -f conda_env.yml && \
    conda clean -a -y

RUN export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
RUN export PATH=$PATH:/home/ubuntu/.local/bin

# Clone wrmXpress into root folder
RUN git clone https://github.com/zamanianlab/wrmXpress.git /opt/wrmXpress
ENV PATH="/opt/wrmXpress:$PATH"

# Activate env by default in container
SHELL ["conda", "run", "-n", "base", "/bin/bash", "-c"]

# Ensure conda env is activated in interactive sessions
RUN echo "conda activate base" >> /root/.bashrc

# Set default to interactive shell (with env auto-activation from .bashrc)
CMD ["bash", "-l"]