# Taken from https://github.com/Homegear/Homegear-Docker/blob/master/rpi-stable/Dockerfile
FROM resin/rpi-raspbian:stretch
MAINTAINER Jan Schulz-Hofen <hassio@0.jan.sh>

RUN apt-get update && apt-get -y install apt-transport-https wget ca-certificates apt-utils gnupg libzip4 libavahi-client3 libavahi-client-dev insserv
RUN wget https://apt.homegear.eu/Release.key && apt-key add Release.key && rm Release.key
RUN echo 'deb https://apt.homegear.eu/Raspbian/ stretch/' >> /etc/apt/sources.list.d/homegear.list
RUN apt-get update && apt-get -y install ntp tzdata homegear homegear-management homegear-webssh homegear-adminui homegear-nodes-core homegear-nodes-extra homegear-homematicbidcos homegear-influxdb vim less htop
RUN rm -f /etc/homegear/dh1024.pem
RUN rm -f /etc/homegear/homegear.crt
RUN rm -f /etc/homegear/homegear.key
RUN cp -R /etc/homegear /etc/homegear.config
RUN cp -R /var/lib/homegear /var/lib/homegear.data

# Inspired by Dockerfile from visevision
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD /start.sh

EXPOSE 2001 2002 2003
