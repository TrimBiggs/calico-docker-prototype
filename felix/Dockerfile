FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y python-zmq iptables ipset wget telnet curl
RUN curl -L http://binaries.projectcalico.org/repo/key | apt-key add -
RUN echo "deb http://binaries.projectcalico.org/repo ./" >> /etc/apt/sources.list

RUN echo "Package: *" >> /etc/apt/preferences
RUN echo "Pin: origin binaries.projectcalico.org" >> /etc/apt/preferences
RUN echo "Pin-Priority: 1001" >> /etc/apt/preferences

RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install -y calico-felix calico-acl-manager

RUN sed -i 's/controller/IP1/' /etc/calico/felix.cfg
RUN sed -i 's/controller/IP1/' /etc/calico/acl_manager.cfg
RUN sed -i 's/#LogSeverityFile.*/LogSeverityFile = DEBUG/' /etc/calico/felix.cfg
RUN sed -i 's/#ResyncIntervalSecs.*/ResyncIntervalSecs = 5/' /etc/calico/felix.cfg
RUN sed -i 's/#MetadataAddr.*/MetadataAddr=None/' /etc/calico/felix.cfg
