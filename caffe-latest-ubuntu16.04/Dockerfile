FROM cuda

RUN apt-get update && \
    apt-get install -y gcc g++ make cmake git \
        libgflags-dev libgoogle-glog-dev libopencv-dev \
        libleveldb-dev libsnappy-dev liblmdb-dev libhdf5-serial-dev \
        libprotobuf-dev protobuf-compiler libopenblas-dev liblapack-dev \
        python-dev python-pip python-numpy gfortran \
        && \
    apt-get install -y --no-install-recommends libboost-all-dev && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/NVIDIA/caffe.git /caffe

RUN mkdir /caffe/build && \
    cd /caffe/build && \
    cmake .. -DBLAS=Open && \
    make -j12

RUN cat /caffe/python/requirements.txt | xargs -n1 pip install

ENV CAFFE_HOME /caffe
