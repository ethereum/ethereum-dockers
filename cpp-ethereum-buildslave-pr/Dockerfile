FROM cptobvious/buildslave-cpp-develop

# Override dependencies from ethereum-dev PPA,
# when building on cptobvious/buildslave-cpp only
# RUN add-apt-repository ppa:ethereum/ethereum-dev
# RUN apt-get update
# RUN apt-get upgrade -y

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
