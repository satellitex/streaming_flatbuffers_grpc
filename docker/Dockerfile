#-----------------------------------------------------------------------
# flatbuf-test - flatbuffers + grpc development container (base image for iroha)
#
# build : docker build -t satellitex/flatbuf-test .
#-----------------------------------------------------------------------
FROM ubuntu:16.04

ENV TEST_HOME /usr/local/iroha
ENV TEST_BUILD ${IROHA_HOME}/build


RUN apt update && apt -y upgrade && \
    apt -y install \
        software-properties-common \
        python-software-properties \
        curl git wget make g++-5 gcc-5 default-jdk \
        libhdf5-serial-dev libleveldb-dev libsnappy-dev \
        liblmdb-dev libssl-dev unzip xsltproc zlib1g-dev \
        autoconf automake libtool jq pkg-config cppcheck \
        valgrind clang-tidy


RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test && \
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-5 20 && \
    update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++-5 20 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 20 && \
    update-alternatives --install /usr/bin/cc cc /usr/bin/gcc-5 20 && \
    curl -sSL https://cmake.org/files/v3.5/cmake-3.5.2-Linux-x86_64.tar.gz | \
      tar -xzC /opt && \
    ln -s /opt/cmake*/bin/c* /usr/local/bin


#install flatbuffer
RUN cd; \
    git clone https://github.com/google/flatbuffers.git; \
    cd flatbuffers; \
    cmake -G "Unix Makefiles"; \
    make; \
    make install; \
    cp ./flatc /usr/bin/

#install grpc
RUN cd; \
    git clone -b v1.3.0 https://github.com/grpc/grpc; \
    cd grpc; \
    git submodule update --init; \
    make; \
    make install


CMD ["/bin/bash"]

