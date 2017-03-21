FROM heamon7/opencv:3.0.0-rc1
MAINTAINER heamon7 <heamon7#g m a i l . c o m>

# Install build-essential, git, wget and other dependencies
RUN rm -rvf /var/lib/apt/lists/*
RUN apt-get update && apt-get install -y \
  build-essential \
  git \
  libopenblas-dev \
  libopencv-dev \
  python-dev \
  python-numpy \
  python-setuptools \
  wget

# Clone MXNet repo and move into it
RUN cd /root && git clone --recursive https://github.com/dmlc/mxnet && cd mxnet && \
# Copy config.mk
  cp make/config.mk config.mk && \
# Set OpenBLAS
  sed -i 's/USE_BLAS = atlas/USE_BLAS = openblas/g' config.mk && \
# Make 
  make -j"$(nproc)"

# Install Python package
RUN cd /root/mxnet/python && python setup.py install

# Add to Python path
RUN echo "export PYTHONPATH=$MXNET_HOME/python:$PYTHONPATH" >> /root/.bashrc

# Install pip
# RUN easy_install -U pip
# Install graphviz and jupyter
RUN apt-get install -y python-dev python-pip libxml2-dev libxslt1-dev zlib1g-dev libffi-dev libssl-dev
RUN pip install graphviz jupyter bpython

# Set ~/mxnet as working directory
WORKDIR /root/mxnet