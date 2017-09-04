FROM ubuntu:16.04

RUN apt-get update \
  && apt-get install -y \
     python3 \
     iproute2 \
     iputils-ping
ADD static/ /var/www/
WORKDIR /var/www

EXPOSE 80
CMD ["python3", "-m", "http.server", "80"]


