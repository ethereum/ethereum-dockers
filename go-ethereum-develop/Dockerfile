FROM cptobvious/go-ethereum-base

RUN go get -v -u -d github.com/ethereum/go-ethereum/ethereum
RUN go get -v -u -d github.com/ethereum/go-ethereum/ethereal

RUN cd $GOPATH/src/github.com/ethereum/go-ethereum && git checkout develop
RUN cd $GOPATH/src/github.com/ethereum/eth-go && git checkout develop

RUN cd $GOPATH/src/github.com/ethereum/go-ethereum/ethereum && go install -v
RUN cd $GOPATH/src/github.com/ethereum/go-ethereum/ethereal && go install -v
