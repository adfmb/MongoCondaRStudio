FROM ubuntu:latest

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN apt-get update --fix-missing && apt-get install -y wget bzip2 ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1 \
    git mercurial subversion

RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/archive/Anaconda3-5.0.0-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh

RUN apt-get install -y curl grep sed dpkg && \
    TINI_VERSION=`curl https://github.com/krallin/tini/releases/latest | grep -o "/v.*\"" | sed 's:^..\(.*\).$:\1:'` && \
    curl -L "https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini_${TINI_VERSION}.deb" > tini.deb && \
    dpkg -i tini.deb && \
    rm tini.deb && \
    apt-get clean

ENV PATH /opt/conda/bin:$PATH

RUN conda install -c anaconda pymongo 
RUN conda install -c conda-forge jupyter_nbextensions_configurator
RUN conda install -c conda-forge jupyter_contrib_nbextensions
RUN conda update scikit-learn
RUN mkdir -p mediapy/notebooks
RUN git clone --no-checkout https://github.com/dragon-analytics/quality-of-life-analysis.git mediapy/notebooks/notebook.tmp
RUN mv mediapy/notebooks/notebook.tmp/.git mediapy/notebooks/
RUN rmdir mediapy/notebooks/notebook.tmp
RUN cd mediapy/notebooks && git reset --hard HEAD



ENTRYPOINT [ "/usr/bin/tini", "--" ]
CMD [ "/bin/bash" ]
