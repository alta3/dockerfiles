FROM ubuntu:16.04

RUN apt-get update \
  && apt-get install -y \
     openssh-server \
     iproute2 \
     iputils-ping \
     vim \
     nano \
     screen \
     tcpdump \
     strongswan \
     curl \
     kmod \
     less
RUN mkdir /var/run/sshd
RUN echo 'root:alta3' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22 500/udp 4500/udp 1812/udp 1813/udp 1645/udp 1646/udp
CMD ["/usr/sbin/sshd", "-D"]


