FROM telegraf:alpine

COPY conf /etc/telegraf
COPY mibs/* /usr/share/snmp/mibs/
CMD         ["--config.file=/etc/loki/loki.yaml"]