FROM cptobvious/buildslave-cpp

RUN apt-get install --fix-missing -y cowbuilder ubuntu-dev-tools dh-autoreconf pkg-kde-tools

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
