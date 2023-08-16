# Use the latest version of Ubuntu
FROM ubuntu:22.04

# Metadata as described above
LABEL maintainer="andreformento.sc@gmail.com" \
      description="Ubuntu with Prometheus and Alertmanager (for amtool)"

# Set environment variables to non-interactive (this prevents some prompts)
ENV DEBIAN_FRONTEND=non-interactive

# Install prerequisites and Prometheus & Alertmanager
RUN apt-get update && \
    apt-get install -y wget tar && \
    # Downloading Prometheus
    wget https://github.com/prometheus/prometheus/releases/download/v2.30.3/prometheus-2.30.3.linux-amd64.tar.gz && \
    tar xvfz prometheus-*.tar.gz && \
    mv prometheus-2.30.3.linux-amd64 prometheus && \
    # Downloading Alertmanager
    wget https://github.com/prometheus/alertmanager/releases/download/v0.23.0/alertmanager-0.23.0.linux-amd64.tar.gz && \
    tar xvfz alertmanager-*.tar.gz && \
    mv alertmanager-0.23.0.linux-amd64 alertmanager
    # Cleaning up
    # apt-get remove --purge -y wget tar && \
    # apt-get autoremove -y && \
    # apt-get clean && \
    # rm -rf /var/lib/apt/lists/* && \
    # rm prometheus-*.tar.gz && \
    # rm alertmanager-*.tar.gz

# Expose port for Prometheus and Alertmanager
EXPOSE 9090 9093

# Set default command
CMD [ "./prometheus/prometheus", "--config.file=./prometheus/prometheus.yml" ]
