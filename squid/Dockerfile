FROM ubuntu:latest

RUN apt update && apt install -y squid

COPY squid.conf /etc/squid/squid.conf

CMD ["squid", "-N", "-d", "1"]
