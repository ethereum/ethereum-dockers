FROM cptobvious/buildslave-cpp-develop

RUN apt-get install xvfb firefox

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
