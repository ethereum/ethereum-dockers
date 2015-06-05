FROM cptobvious/buildslave-go-develop

RUN apt-get install -qy wget lzip gcc-arm-linux-gnueabi libc6-dev-armel-cross gcc-multilib m4

ENV DIST_LINUX_ARM go1.4.2.linux-arm~armv5-1.tar.gz
ENV DIST_LINUX_ARM_URL http://dave.cheney.net/paste/$DIST_LINUX_ARM
ENV DIST_LINUX_ARM_SHA1 1bcfc8ef9c2aa381722b71b8c8d83cb58e973116

ENV DIST_LINUX_GMP gmp-6.0.0a
ENV DIST_LINUX_GMP_URL https://gmplib.org/download/gmp/$DIST_LINUX_GMP.tar.lz
ENV DIST_LINUX_GMP_SHA256 8890803a2715d592eac37dca630e36b470f047eb5ab1efe38d323b02a99ac232

RUN mkdir /go-arm
RUN mkdir /deps

WORKDIR /go-arm
RUN \
  wget $DIST_LINUX_ARM_URL && \
  echo "$DIST_LINUX_ARM_SHA1  $DIST_LINUX_ARM" > $DIST_LINUX_ARM.sum && \
  sha1sum -c $DIST_LINUX_ARM.sum && \
  tar -C /usr/local --wildcards -xzf $DIST_LINUX_ARM go/pkg/linux_arm* && \
  GOOS=linux GOARCH=arm /usr/lib/go/pkg/tool/linux_amd64/dist bootstrap && \
  rm $DIST_LINUX_ARM && \
  rm $DIST_LINUX_ARM.sum

WORKDIR /deps
RUN \
  wget $DIST_LINUX_GMP_URL && \
  lzip -d $DIST_LINUX_GMP.tar.lz && \
  echo "$DIST_LINUX_GMP_SHA256  $DIST_LINUX_GMP.tar" > $DIST_LINUX_GMP.tar.sum && \
  sha256sum -c $DIST_LINUX_GMP.tar.sum && \
  tar -xf $DIST_LINUX_GMP.tar && \
  rm $DIST_LINUX_GMP.tar && \
  rm $DIST_LINUX_GMP.tar.sum

ENV CC arm-linux-gnueabi-gcc
ENV HOST arm-linux
ENV PREFIX /usr/local/arm
WORKDIR /deps/gmp-6.0.0
RUN ./configure --disable-shared --host=$HOST --prefix=$PREFIX
RUN make -j install

WORKDIR /

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
