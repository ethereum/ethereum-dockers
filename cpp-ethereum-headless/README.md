# Dockerfile for cpp-ethereum-headless
Dockerfile to build a headless bleeding edge cpp-ethereum docker image from source

    docker build -t cppeth .

Run a simple peer server

    docker run -i cppeth -m off -o peer -x 256
