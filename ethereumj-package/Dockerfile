FROM cptobvious/ethereumj-base

RUN git clone --depth=1 https://github.com/ethereum/ethereumj
RUN cd ethereumj/ethereumj-core && mvn package && mvn install
RUN cd ethereumj/ethereumj-studio && mvn package
