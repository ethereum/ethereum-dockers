FROM cptobvious/pyethereum-base

RUN git clone --depth=1 https://github.com/ethereum/pyethereum.git

RUN cd pyethereum && pip install -e .

WORKDIR /pyethereum
