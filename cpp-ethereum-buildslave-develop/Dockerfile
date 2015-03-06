FROM cptobvious/buildslave-cpp

# Override dependencies from ethereum-dev PPA
RUN add-apt-repository ppa:ethereum/ethereum-dev
RUN apt-get update
RUN apt-get upgrade -y

# Qt5 for develop
RUN apt-get install -qy mesa-common-dev libglu1-mesa-dev
RUN add-apt-repository ppa:beineri/opt-qt541-trusty
RUN apt-get update
RUN apt-get install -qy qt54quickcontrols qt54webengine
ENV LD_LIBRARY_PATH /opt/qt54/lib/x86_64-linux-gnu:/opt/qt54/lib
ENV PKG_CONFIG_PATH /opt/qt54/lib/pkgconfig
ENV QTDIR=/opt/qt54
RUN PATH=$QTDIR/bin:$PATH
# RUN /bin/bash -c "source /opt/qt54/bin/qt54-env.sh"

RUN apt-get install -qy pkg-config libpcre3-dev libpcre++-dev

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
