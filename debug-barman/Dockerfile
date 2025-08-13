# Start from Debian Slim so it matches CNPG base OS
FROM debian:12-slim

# Install useful tools at build time
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        dnsutils \
        iputils-ping \
        iproute2 \
        traceroute \
        less \
        vim \
        awscli \
        python3 \
        python3-pip \
        postgresql-client \
        barman-cli \
        barman-cli-cloud \
        openssl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# python3-venv python3-pip
# python3 -m venv /opt/venv
#ENV PATH="/opt/venv/bin:$PATH"
#RUN pip install --no-cache-dir barman

# Create non-root user (UID 1000 matches many restricted clusters)
RUN useradd -u 1000 -m debuguser

# Switch to non-root
USER 1000

# Default command keeps the pod alive
CMD ["/bin/sh", "-c", "echo 'Debug pod running with aws- and barmancli'; tail -f /dev/null"]
