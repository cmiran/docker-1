FROM debian

RUN apt-get update -q \
&& DEBIAN_FRONTEND=noninteractive apt-get install -yq --no-install-recommends \
ca-certificates \
openssh-server \
curl \
postfix

WORKDIR /
RUN curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh

RUN bash script.deb.sh

RUN apt-get update && EXTERNAL_URL="http://gitlab.example.com" apt-get install -yq gitlab-ce

# Missing Time Zone Data /usr/share/zoneinfo
# https://gitlab.com/gitlab-org/omnibus-gitlab/issues/2229
RUN apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 22 80 443

ADD https://gist.githubusercontent.com/cmiran/10290446c9a59f00ae54a47e6944a423/raw/52c4dee5e44f2ace22ba79de49ec9f78c5ccebec/gitlab-entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

CMD [ "bash", "/entrypoint.sh" ]

# iptables iptables -A INPUT -p tcp -i eth0 --dport http -j ACCEPT
# iptables iptables -A INPUT -p tcp -i eth0 --dport https -j ACCEPT
# iptables -A INPUT -p tcp -i eth0 --dport ssh -j ACCEPT
# https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-gitlab-on-debian-9
# docker build -t ex03 .
# docker run -it --rm -p 80:80 -p 21:22 --privileged ex03

# https://github.com/TheScottishFly/Docker-1/tree/master/01_dockerfiles/ex03
# https://github.com/rizkyario/42-docker-1/blob/master/01_dockerfiles/ex03/Dockerfile
