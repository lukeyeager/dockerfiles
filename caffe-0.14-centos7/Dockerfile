FROM nvidia/cuda:7.0-devel-centos7

RUN yum install -y epel-release

RUN yum install -y gcc gcc-c++ make cmake \
    git \
    gflags-devel glog-devel \
    opencv-devel \
    boost-devel \
    openblas-devel \
    protobuf-devel \
    leveldb-devel snappy-devel hdf5-devel lmdb-devel

RUN git clone https://github.com/NVIDIA/caffe.git ~/caffe --branch caffe-0.14

RUN mkdir ~/caffe/build && \
    cd ~/caffe/build && \
    cmake .. -DBLAS=Open && \
    make -j4
