FROM ubuntu:xenial

LABEL com.nvidia.volumes.needed="nvidia_driver"

RUN apt-get update && \
    apt-get install -y wget perl && \
    rm -rf /var/lib/apt/lists/*

RUN wget http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda_7.5.18_linux.run -nv -O ~/cuda.run && \
    sh ~/cuda.run --silent --toolkit --samples --override && \
    rm ~/cuda.run

# Disable gcc version check
RUN sed -e '/unsupported GNU version/ s/^\/*/\/\//' -i /usr/local/cuda/include/host_config.h

RUN echo "/usr/local/cuda/lib" >> /etc/ld.so.conf.d/cuda.conf && \
    echo "/usr/local/cuda/lib64" >> /etc/ld.so.conf.d/cuda.conf && \
    ldconfig

RUN echo "/usr/local/nvidia/lib" >> /etc/ld.so.conf.d/nvidia.conf && \
    echo "/usr/local/nvidia/lib64" >> /etc/ld.so.conf.d/nvidia.conf

ENV PATH /usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64:${LD_LIBRARY_PATH}
