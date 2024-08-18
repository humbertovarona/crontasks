FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    cron \
    wget \
    curl \
    axel \
    wget2 \
    aria2 \
    lftp \
    httrack \
    mc \
    openssh-client \
    ftp \
    rsync \
    dash \
    zsh \
    nano \
    gawk \
    grep \
    sed \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /usr/src/app/shared/data /usr/src/app/crontasks /usr/src/app/scripts

RUN touch /var/log/cron.log

CMD ["sh", "-c", "chmod +x /usr/src/app/scripts/* && cp /usr/src/app/crontasks/crontab /etc/cron.d/my-crontab && chmod 0644 /etc/cron.d/my-crontab && crontab /etc/cron.d/my-crontab && cron && tail -f /var/log/cron.log"]
