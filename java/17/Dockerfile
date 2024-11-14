#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM --platform=$TARGETOS/$TARGETARCH eclipse-temurin:17-jdk-jammy
LABEL author="Matthew Penner" maintainer="matthew@pterodactyl.io"
LABEL org.opencontainers.image.source="https://github.com/iShotFT/pterodactyl-docker-reg"
LABEL org.opencontainers.image.licenses=MIT

# Set environment variables for native library loading
ENV LD_LIBRARY_PATH=/usr/lib:/usr/lib/x86_64-linux-gnu:/home/container
ENV JAVA_TOOL_OPTIONS="-Djava.library.path=/usr/lib:/usr/lib/x86_64-linux-gnu:/home/container"

RUN apt-get update -y \
    && apt-get install -y \
        lsof \
        curl \
        ca-certificates \
        openssl \
        git \
        tar \
        sqlite3 \
        fontconfig \
        libfreetype6 \
        tzdata \
        iproute2 \
        libstdc++6 \
        binutils \
        build-essential \
        libc6-dev \
        libgcc1 \
        libc6 \
        libssl-dev \
        libffi-dev \
        libxml2-dev \
        zlib1g-dev \
        libbz2-dev \
        libxrender1 \
        libxtst6 \
        libxi6 \
        libxext6 \
        libxrender1 \
        mesa-utils \
        xvfb \
    && ldconfig \
    && useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

# Create directory for native libraries
RUN mkdir -p /home/container/natives

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]