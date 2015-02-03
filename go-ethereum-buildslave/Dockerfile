FROM cptobvious/go-ethereum-base

# Qt5 for master
RUN add-apt-repository ppa:ubuntu-sdk-team/ppa
RUN apt-get update
RUN apt-get install -qy ubuntu-sdk
RUN apt-get install -qy qtbase5-dev
RUN apt-get install -qy qtbase5-private-dev qtdeclarative5-private-dev libqt5opengl5-dev

# Buildslave dependencies
RUN apt-get install --fix-missing -y apt-utils python-pip python-dev supervisor git inotify-tools

# Clone latest buildbot
RUN git clone https://github.com/buildbot/buildbot.git

# Install buildbot
RUN cd buildbot && git checkout eight && pip install -e slave
RUN pip install pip-tools requests
# RUN pip-review -a

# Create buildslave
RUN buildslave create-slave -r -l 3 -s 512000 slave build.ethdev.com:9989 dockerslave pass
# Add manually set buildslave config, use .sample file or previously created buildslave config
ADD buildbot.tac slave/buildbot.tac

# Set slave/info/admin and slave/info/host
RUN echo "caktux <caktux@gmail.com>" > slave/info/admin
RUN echo `lsb_release -ds` > slave/info/host

# Setup supervisord
RUN /bin/echo -e "[supervisord]\n\
nodaemon=true\n\
\n\
[program:buildslave]\n\
directory=/slave\n\
user=root\n\
command=twistd --nodaemon --no_save -y buildbot.tac" > /etc/supervisor/conf.d/buildbot.conf

# CMD ["start", "slave"]
# ENTRYPOINT ["buildslave"]
CMD ["-n", "-c", "/etc/supervisor/conf.d/buildbot.conf"]
ENTRYPOINT ["/usr/bin/supervisord"]
