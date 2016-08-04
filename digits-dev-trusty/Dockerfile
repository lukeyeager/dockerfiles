FROM nvidia/cuda:7.5-cudnn5-devel-ubuntu14.04

RUN apt-get update -q
RUN apt-get install -q -y --force-yes --no-install-recommends \
        build-essential \
        ca-certificates \
        cmake \
        curl \
        git \
        gfortran \
        graphviz \
        gunicorn \
        libboost-python-dev \
        libboost-system-dev \
        libboost-thread-dev \
        libgflags-dev \
        libgoogle-glog-dev \
        libhdf5-serial-dev \
        libleveldb-dev \
        liblmdb-dev \
        libopenblas-dev \
        libopencv-dev \
        libprotobuf-dev \
        libsnappy-dev \
        protobuf-compiler \
        python-all-dev \
        python-crypto \
        python-flask \
        python-flaskext.wtf \
        python-gevent \
        python-h5py \
        python-matplotlib \
        python-numpy \
        python-opencv \
        python-pil \
        python-pip \
        python-protobuf \
        python-pydot \
        python-scipy \
        python-skimage \
        python-sklearn \
        python-virtualenv \
        software-properties-common \
        wget \
        vim

RUN add-apt-repository ppa:luke-yeager/digits
RUN apt-get update -q
RUN apt-get install -q -y --force-yes --no-install-recommends \
        python-engineio \
        python-flaskext.wtf \
        python-flaskext.socketio \
        python-lmdb \
        python-socketio2 \
        python-wtforms

ADD .bust-cache /tmp

# Build caffe
RUN git clone https://github.com/NVIDIA/caffe.git /workdir/caffe
RUN mkdir /workdir/caffe/build
WORKDIR /workdir/caffe/build
RUN cmake .. -DBLAS=Open \
        -DCUDA_ARCH_BIN="52" -DCUDA_ARCH_PTX="35" -DCUDA_ARCH_NAME=Manual
RUN make -j12

# Get DIGITS
RUN git clone https://github.com/NVIDIA/DIGITS.git /workdir/digits
WORKDIR /workdir/digits
