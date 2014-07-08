FROM go-ethereum-base

RUN go get -d github.com/obscuren/serpent-go
RUN cd $GOPATH/src/github.com/obscuren/serpent-go && git submodule init && git submodule update

RUN go get -u github.com/ethereum/go-ethereum/ethereum
RUN go get -u github.com/ethereum/go-ethereum/ethereal
