FROM continuumio/miniconda3
MAINTAINER mzamanian@wisc.edu

# install (nf tracing)
RUN apt-get update && apt-get install -y procps

# install conda packages
COPY conda_env.yml .
RUN \
   conda env update -n root -f conda_env.yml \
&& conda clean -a

#install cellranger
RUN wget -O cellranger-5.0.1.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-5.0.1.tar.gz?Expires=1613842715&Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9jZi4xMHhnZW5vbWljcy5jb20vcmVsZWFzZXMvY2VsbC1leHAvY2VsbHJhbmdlci01LjAuMS50YXIuZ3oiLCJDb25kaXRpb24iOnsiRGF0ZUxlc3NUaGFuIjp7IkFXUzpFcG9jaFRpbWUiOjE2MTM4NDI3MTV9fX1dfQ__&Signature=NEDNdXe-Yoxl9bl~VEdl9JJeZmzzF7HceslKEP5ooPEg7U8Tz5qCO-Ix2fCNPx98BK3mZ5gahwd9McMQij~9upoW6lC5fkeJdH4uzn4fe1CD6eY1zYUN~g-qWH69WMM2tSmaw1NMDurFoF6Tp2MkV2NcsJq54riL8HIIG~Z~heYl~bQZ~u0Ql-exXPOF-PO8kVJiwaeQ290MMtekt4f2gozI51FQwBWbHywMlKR5uoa107os15ZztIE4KC60~fk4~KUAyJaDvN8kgjw9dtO~iN-agsw~Sbj5xVFblk68UZVaiH5y7gGyYuMn7mft8x2g6hlVIvu-zI6ZdhO3Qub09w__&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA"

RUN tar -xzvf cellranger-5.0.1.tar.gz
ENV PATH=/cellranger-5.0.1:$PATH
