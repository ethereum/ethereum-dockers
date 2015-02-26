FROM cptobvious/buildslave-cpp-develop

RUN apt-get install --fix-missing -y xvfb
RUN apt-get install --fix-missing -y firefox=28.0+build2-0ubuntu2
RUN pip install nose nose-html coverage selenium

# Overwrite buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac
