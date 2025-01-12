# Postgres HA patroni Docker image

Image that bundles official Docker image from Potgres and installs on top of it:
- patroni (support for etcd, consul): https://patroni.readthedocs.io/en/latest/index.html
- pgBackRest


## Why?
Because there is no official image from Patroni and solutions like [Spilo](https://github.com/zalando/spilo) have inconsistent documentation 
