ARG POSTGRES_VERSION=16

FROM postgres:${POSTGRES_VERSION}

# Switch to root for installing dependencies
USER root

# Install dependencies, Patroni, and pgBackRest
RUN apt-get update && apt-get install -y \
    python3-psycopg2 \
    procps \
    patroni \
    python3-etcd3 \
    python3-consul \
    pgbackrest \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create necessary directories and set permissions
RUN mkdir -p /var/lib/postgresql/config \
    && chown postgres:postgres -R /var/lib/postgresql/ \
    && chmod -R 700 /var/lib/postgresql/

# Revert to the default postgres user
USER postgres

# Expose PostgreSQL and Patroni API ports
EXPOSE 5432 8008

# Set the default command for Patroni
CMD ["patroni", "/etc/patroni/patroni.yml"]
