FROM debian

EXPOSE 9987/udp 10011 30033

RUN	adduser teamspeak && \
	su teamspeak && \
	apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y wget bzip2

WORKDIR /home/teamspeak

RUN wget http://dl.4players.de/ts/releases/3.8.0/teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
	tar -xvf teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
	rm teamspeak3-server_linux_amd64-3.8.0.tar.bz2

ENV TS3SERVER_LICENSE=accept

WORKDIR teamspeak3-server_linux_amd64

CMD sh ts3server_minimal_runscript.sh
