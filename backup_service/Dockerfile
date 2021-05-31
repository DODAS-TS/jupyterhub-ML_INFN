FROM ubuntu:20.04

RUN DEBIAN_FRONTEND=noninteractive apt update && apt upgrade -y && apt install -y rsnapshot
COPY rsnapshot.conf /etc/
COPY rsnapshot /etc/cron.d/
RUN chmod 644 /etc/cron.d/rsnapshot && crontab /etc/cron.d/rsnapshot
RUN /bin/bash -c "mkdir -p /source"
# Smoke test
RUN rsnapshot configtest

CMD ["cron", "-f"]
