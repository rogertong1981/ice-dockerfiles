FROM ubuntu:14.04

MAINTAINER ZeroC, Inc. docker-maintainers@zeroc.com

ENV ICEGRID_VERSION 3.6.2

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv 5E6DA83306132997 \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
    && echo "deb http://zeroc.com/download/apt/ubuntu14.04 stable main" >> /etc/apt/sources.list.d/ice.list \
    && echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
            zeroc-icegrid=${ICEGRID_VERSION}-* \
    && apt-get install --no-install-recommends --no-install-suggests -y mono-complete \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 4061 4062

VOLUME ["/var/lib/ice/icegrid"]

ENTRYPOINT ["/usr/bin/icegridnode", "--Ice.Config=/etc/icegridnode.conf", "--IceGrid.Node.Data=/var/lib/ice/icegrid"]
