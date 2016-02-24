FROM caffe

RUN apt-get update && \
    apt-get install -y python-dev python-pip graphviz \
        python-pil python-numpy python-scipy python-protobuf python-gevent python-flask python-flaskext.wtf gunicorn python-h5py \
        && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/NVIDIA/DIGITS.git /digits

RUN cat /digits/requirements.txt | xargs -n1 pip install

EXPOSE 34448
WORKDIR /digits
ENTRYPOINT ["./digits-server"]
