FROM cptobvious/pyethereum-base

RUN git clone --depth=1 https://github.com/ethereum/pyethereum.git
RUN cd pyethereum && python ../bootstrap.py
RUN cd pyethereum && ./bin/buildout
RUN cd pyethereum && ./bin/buildout -c develop.cfg

WORKDIR /pyethereum
