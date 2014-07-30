FROM cptobvious/cpp-ethereum-base

RUN git clone --depth=1 --branch=develop https://github.com/ethereum/tests
RUN git clone --depth=1 --branch=develop https://github.com/ethereum/cpp-ethereum

RUN mkdir cpp-ethereum/build
RUN cd cpp-ethereum/build && cmake .. -DCMAKE_BUILD_TYPE=Release -DHEADLESS=1 && make -j $(cat /proc/cpuinfo | grep processor | wc -l) && make test && make install
RUN ldconfig
