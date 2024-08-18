FROM alpine:20240606

RUN apk update && apk add --no-cache \
    python3 \
    py3-pip \
    openrc \
    wget \
    curl \
    axel \
    aria2 \
    lftp \
    mc \
    openssh-client \
    rsync \
    dash \
    zsh \
    bash \
    nano \
    gawk \
    grep \
    sed

RUN mkdir -p /usr/src/app/shared/data /usr/src/app/crontasks /usr/src/app/scripts

RUN touch /var/log/cron.log

RUN sed -i 's|/bin/ash|/bin/bash|' /etc/passwd

CMD ["sh", "-c", "chmod +x /usr/src/app/scripts/* && cp /usr/src/app/crontasks/crontab /etc/crontabs/root && chmod 0644 /etc/crontabs/root && crond -f && tail -f /var/log/cron.log"]
