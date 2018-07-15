FROM ubuntu
LABEL maintainer="Michael Bartling <michael.bartling15@gmail.com>"

RUN apt-get update && \
    apt-get install -y \
    libgtest-dev \
    git \
    cmake \
    gcc \
    wget \
    g++ 

# Install latest CMAKE
ARG version=3.11
ARG build=0

RUN apt-get purge -y cmake && \
    mkdir /tmp/cmake && \
    cd /tmp/cmake && \
    wget https://cmake.org/files/v$version/cmake-$version.$build.tar.gz && \
    tar -xzvf cmake-$version.$build.tar.gz && \
    cd cmake-$version.$build/ && \
    ./bootstrap && \
    make && \
    make install && \
    rm -rf /tmp/cmake

# configure GTEST
RUN cd /usr/src/gtest && \
    cmake CMakeLists.txt && \
    make && \
    cp *.a /usr/lib && \
    mkdir /usr/local/lib/gtest && \
    ln -s /usr/lib/libgtest.a /usr/local/lib/gtest/libgtest.a && \
    ln -s /usr/lib/libgtest_main.a /usr/local/lib/gtest/libgtest_main.a


