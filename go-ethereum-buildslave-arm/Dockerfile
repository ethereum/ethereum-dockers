FROM cptobvious/buildslave-go-develop

RUN apt-get install -qy wget lzip gcc-5-arm-linux-gnueabi gcc-5-multilib libc6-dev-armel-cross m4

ENV DIST_LINUX_GMP gmp-6.0.0a
ENV DIST_LINUX_GMP_URL https://gmplib.org/download/gmp/$DIST_LINUX_GMP.tar.lz
ENV DIST_LINUX_GMP_SHA256 8890803a2715d592eac37dca630e36b470f047eb5ab1efe38d323b02a99ac232

RUN mkdir /deps

WORKDIR /deps
RUN \
  wget $DIST_LINUX_GMP_URL && \
  lzip -d $DIST_LINUX_GMP.tar.lz && \
  echo "$DIST_LINUX_GMP_SHA256  $DIST_LINUX_GMP.tar" > $DIST_LINUX_GMP.tar.sum && \
  sha256sum -c $DIST_LINUX_GMP.tar.sum && \
  tar -xf $DIST_LINUX_GMP.tar && \
  rm $DIST_LINUX_GMP.tar && \
  rm $DIST_LINUX_GMP.tar.sum

ENV CC arm-linux-gnueabi-gcc-5
ENV HOST arm-linux-gnueabi
ENV PREFIX /usr/local/arm
WORKDIR /deps/gmp-6.0.0
RUN ./configure --disable-shared --host=$HOST --prefix=$PREFIX
RUN make -j install

WORKDIR /

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
