FROM continuumio/miniconda3

MAINTAINER Olgiati Nahuel <nahuelolgiati@hotmail.com>

RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install -y wget libx11-dev libx11-dev:i386 libxft-dev libxft-dev:i386 && \
    apt-get install -y libc6:i386 libz1:i386 libncurses5:i386 libbz2-1.0:i386 libuuid1:i386 libxcb1:i386 libxmu6:i386 && \
    apt-get -y clean all

RUN conda update -n base -c defaults conda && \
    conda update -y --all && \
    conda config --add channels http://ssb.stsci.edu/astroconda && \
    conda create -n iraf27 python=2.7 iraf-all pyraf-all stsci iraf-os-libs -c astroconda && \
    conda clean -y --all

ARG USER_ID
ARG GROUP_ID

RUN groupadd -f -g ${GROUP_ID} iraf && \
    useradd -l -u ${USER_ID} -g iraf iraf

RUN mkdir -p /home/iraf && chown -R iraf:iraf /home/iraf

RUN /bin/bash -c "/opt/conda/bin/conda init bash && source ~/.bashrc"
RUN /bin/bash -c 'cd /home/iraf && source .bashrc && conda activate iraf27 && printf "xgterm\n" | mkiraf'

USER iraf
ENV HOME /home/iraf
