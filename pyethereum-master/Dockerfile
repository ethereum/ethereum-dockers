FROM cptobvious/pyethereum-base

RUN git clone --depth=1 https://github.com/ethereum/pyethereum.git

RUN mkdir -p /.buildout/eggs /.buildout/extends /.buildout/cache
RUN /bin/echo -e "[buildout]\n\
eggs-directory = /.buildout/eggs\n\
download-cache = /.buildout/cache\n\
extends-cache = /.buildout/extends\n\
" > /.buildout/default.cfg

RUN cd pyethereum && python ../bootstrap.py
RUN cd pyethereum && ./bin/buildout
RUN cd pyethereum && ./bin/buildout -c develop.cfg

WORKDIR /pyethereum
