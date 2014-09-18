FROM cptobvious/go-ethereum-base

RUN go get -v -u gopkg.in/qml.v1
RUN go get -v -u -d github.com/ethereum/go-ethereum/ethereum
RUN go get -v -u -d github.com/ethereum/go-ethereum/Mist
RUN go get -v -u -d github.com/obscuren/serpent-go

RUN cd $GOPATH/src/github.com/obscuren/serpent-go && git submodule update --init
RUN cd $GOPATH/src/github.com/obscuren/serpent-go && go install -v

RUN cd $GOPATH/src/github.com/ethereum/go-ethereum && git checkout develop
RUN cd $GOPATH/src/github.com/ethereum/eth-go && git checkout develop

RUN cd $GOPATH/src/github.com/ethereum/go-ethereum/ethereum && go install -v
RUN cd $GOPATH/src/github.com/ethereum/go-ethereum/Mist && go install -v

