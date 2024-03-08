FROM prom/prometheus:latest

CMD [ "--config.file=/etc/prometheus/prometheus.yml", \
     "--storage.tsdb.path=/prometheus", \
     "--web.console.libraries=/usr/share/prometheus/console_libraries", \
     "--web.console.templates=/usr/share/prometheus/consoles", \
     "--storage.tsdb.retention.time=10d", \
     "--storage.tsdb.retention.size=30GB" ]