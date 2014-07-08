# Dockerfile for cpp-ethereum-headless
Dockerfile to build a headless bleeding edge cpp-ethereum docker image from source:

    docker build -t cpp-ethereum-headless .

Run a simple peer server:

    docker run -i cpp-ethereum-headless eth -m off -o peer -x 256
