FROM ubuntu:latest
LABEL authors="AvaTrimble"

USER root
#
# Download docker image: docker pull ubuntu
# Start interactive container: docker run -it ubuntu /bin/bash
# docker build . -t py10-gdal3.8.5:v1
RUN \
# Install runtime dependencies
    apt-get update \
    && apt-get install -y \
    wget \
    build-essential \
    checkinstall \
    libssl-dev \
    libsqlite3-dev \
    sqlite3 \
    libgdbm-dev \
    libbz2-dev \
    libffi-dev \
    zlib1g-dev \
    curl \
    unzip \
    make \
    cmake \
    git \
    net-tools \
    libproj-dev \
    libxml2-dev \
    libgeos-dev \
    libnetcdf-dev \
    libpoppler-dev \
    libspatialite-dev \
    libhdf4-alt-dev \
    libhdf5-serial-dev \
    libopenjp2-7-dev
    ## && rm -rf /var/lib/apt/lists/*

RUN \
    wget https://www.python.org/ftp/python/3.10.10/Python-3.10.10.tgz && \
    tar xzf Python-3.10.10.tgz && \
    cd Python-3.10.10 && \
    ./configure --enable-optimizations && \
    make install

RUN \
    # Install numpy
    pip3 install numpy && \
    # Build against PROJ master, requires libsqlite3,
    wget "http://download.osgeo.org/proj/proj-9.3.1.tar.gz" && \
    tar -xzf "proj-9.3.1.tar.gz" && \
    mv proj-9.3.1 proj && \
    cd proj && \
    mkdir build && \
    cd build && \
    cmake .. && \
    cmake --build . && \
    cmake --build . --target install && \
    cd /

RUN wget https://github.com/OSGeo/gdal/releases/download/v3.8.5/gdal-3.8.5.tar.gz  && \
     tar -xvf gdal-3.8.5.tar.gz && \
     cd gdal-3.8.5 && \
     mkdir build && \
     cd build && \
     cmake .. && \
     cmake --build . -j 8 && \
     cmake --build . --target install && \
     echo /usr/local/lib64 >> /etc/ld.so.conf && \
     ldconfig && \
     ogrinfo --version && \
     gdal-config --version && \
     cd /