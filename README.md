# Docker images

## Nextcloud Apache full
based on https://github.com/nextcloud/docker/blob/master/.examples/README.md#full
contains:
- ffmpeg, intel vaapi
- crontab
- `PHP_MEMORY_LIMIT` set to 1GB
- [video preview generation](https://github.com/nextcloud/previewgenerator) app already installed and crontab configured
- vim

**Install**

```
docker pull ghcr.io/dtila/dockers/nexcloud-ha-crontab:latest
```

