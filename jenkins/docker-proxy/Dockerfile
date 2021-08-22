FROM clearlinux:latest
LABEL maintainer="gregmix88@gmail.com"

RUN swupd update && swupd bundle-add socat

VOLUME /var/run/docker.sock

# docker tcp port
EXPOSE 2375

ENTRYPOINT ["socat", "TCP-LISTEN:2375,reuseaddr,fork","UNIX-CLIENT:/var/run/docker.sock"]
