FROM debian

RUN apt-get update\
	&& apt-get upgrade -y\
	&& apt-get install curl -y\
	&& apt-get install bzip2\
	&& useradd teamspeak

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

WORKDIR /home/teamspeak

RUN curl -O http://dl.4players.de/ts/releases/3.5.0/teamspeak3-server_linux_amd64-3.5.0.tar.bz2\
	&& tar -xjvf teamspeak3-server_linux_amd64-3.5.0.tar.bz2\
	&& rm -rf teamspeak3-server_linux_amd64-3.5.0.tar.bz2

WORKDIR /home/teamspeak/teamspeak3-server_linux_amd64

USER teamspeak

CMD ["sh","ts3server_minimal_runscript.sh","license_accepted=1"]
