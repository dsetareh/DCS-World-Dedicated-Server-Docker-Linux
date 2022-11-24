# DCS-server-docker Dockerfile
# From: https://old.reddit.com/r/hoggit/comments/ns6g7j/you_can_run_dedicated_server_on_linux_here_is_how/

FROM dorowu/ubuntu-desktop-lxde-vnc:focal

ENV DEBIAN_FRONTEND noninteractive
ENV LANG en_US.utf8

RUN set -ex; apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4EB27DB2A3B88B8B; apt-get update; apt-get install -y locales nano; rm -rf /var/lib/apt/lists/*; localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8

# Install basics and setup locale
RUN set -ex; \
apt-get update; \
apt-get install -y locales nano vim htop; \
rm -rf /var/lib/apt/lists/*; \
localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8

## Add Wine
RUN dpkg --add-architecture i386
RUN wget -nc https://dl.winehq.org/wine-builds/winehq.key ; apt-key add winehq.key ; apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main'
RUN apt update -y ; apt install -y --install-recommends winehq-stable

## Add Lutris
RUN add-apt-repository ppa:lutris-team/lutris; \
apt update -y; \
apt install -y lutris

## Add xdotool
RUN apt-get install -y xdotool

## Cleanup apt cache
RUN apt-get clean; \
rm -rf /var/lib/apt/lists/*

ENV PATH "$PATH:/usr/games"