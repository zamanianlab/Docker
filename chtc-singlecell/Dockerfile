FROM continuumio/miniconda3
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update && apt-get install -y procps

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a

# install cellranger
RUN wget -O cellranger-6.1.2.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-6.1.2.tar.gz?Expires=1639995411&Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9jZi4xMHhnZW5vbWljcy5jb20vcmVsZWFzZXMvY2VsbC1leHAvY2VsbHJhbmdlci02LjEuMi50YXIuZ3oiLCJDb25kaXRpb24iOnsiRGF0ZUxlc3NUaGFuIjp7IkFXUzpFcG9jaFRpbWUiOjE2Mzk5OTU0MTF9fX1dfQ__&Signature=dxUcsHRyGBWoPLpZgXs7GETslS8Cqk9X4hTfHKoSvUrWATGO9YbSmbnE5hnYYaKaS1zL-f-cPTJ2BzBewEXfFp8WZ8DoWFN7EnzWPhLokXnOsSluG~~aEl-vbIK3yukxR~L0sY8bmoO7F~qhykr07JItr3oSh25Y-D5tysScJecRY4HL-xmgISQmdeI5JRo7WeguGimBlMs6oDazGe2hxpaSz8U7gMTyS6XXbYYi6UI-Yxvn0NbROaV6jKmW7fNR9uFMnSLddhUgp4Q3sGJ3oWq~939VoT7Yp6QwVQb50YSgAQReOzO7EaK0yX~dVRSccSFKqL-Yemw2bGoXpW1eEQ__&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA"

RUN tar -xzvf cellranger-6.1.2.tar.gz
ENV PATH=/cellranger-6.1.2:$PATH
