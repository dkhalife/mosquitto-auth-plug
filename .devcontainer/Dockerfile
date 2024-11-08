#-------------------------------------------------------------------------------------------------------------
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License. See https://go.microsoft.com/fwlink/?linkid=2090316 for license information.
#-------------------------------------------------------------------------------------------------------------
FROM ubuntu:24.10

ARG MOSQUITTO_VERSION=2.0.20

# Configure apt
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        apt-utils procps lsb-release libcurl4-openssl-dev \
        libwebsockets-dev libc-ares2 libmysqlclient-dev \
        libc-ares-dev openssl uuid uuid-dev wget build-essential git libcjson1 libcjson-dev ;
RUN wget --no-check-certificate http://mosquitto.org/files/source/mosquitto-${MOSQUITTO_VERSION}.tar.gz;
RUN tar xzvf mosquitto-${MOSQUITTO_VERSION}.tar.gz;
RUN cd mosquitto-${MOSQUITTO_VERSION} \
    && make WITH_WEBSOCKETS=yes \
    && make install \
    && cd .. \
    && rm -fr mosquitto-${MOSQUITTO_VERSION}* ;
RUN apt-get autoremove -y \
    && apt-get clean -y;

# Set the default shell to bash instead of sh
ENV SHELL /bin/bash