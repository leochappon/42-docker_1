FROM debian

RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install curl -y
RUN apt-get install bzip2 -y

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

RUN useradd teamspeaker
WORKDIR /opt/teamspeak

RUN curl http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 > teamspeak3.tar.bz2
RUN tar -xjvf teamspeak3.tar.bz2
RUN rm -rf teamspeak3.tar.bz2
WORKDIR teamspeak3-server_linux_amd64
USER teamspeaker

ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]

# docker build . -t ts3
# docker run -it --publish=9987:9987/udp --publish=30033:30033/tcp --publish=10011:10011/tcp --name teamspeak3 ts3
