FROM gcc:11.2.0

# Install cpputest
WORKDIR /home/cpputest

RUN git clone --depth 1 --branch v4.0 https://github.com/cpputest/cpputest.git .
RUN autoreconf . -i && \
    ./configure && \
    make tdd && \
    make install 

ENV CPPUTEST_HOME="/home/cpputest"

# Install leagcy-build
WORKDIR /home/legacy-build
RUN git clone --depth 1 https://github.com/jwgrenning/legacy-build.git .
RUN git submodule update --init --recursive
ENV LEGACY_BUILD="/home/legacy-build"
RUN echo '#!/bin/bash' >>/usr/bin/legacy-build && \
    echo '/home/legacy-build/legacy-build.sh' >>/usr/bin/legacy-build && \
        chmod +x /usr/bin/legacy-build
RUN echo 'echo run make or legacy-build' >> ~/.bashrc

WORKDIR /home/src
